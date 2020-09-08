<template>
<div class="landing-bg">
<nav class="navbar navbar-expand-lg navbar-light d-flex sticky-top pb-lg-0 pt-0 my-0 conference-bg" id="header" style="">
<ul id="headmenu" class="navbar-nav  w-100 py-3">
<div class="container-fluid px-5 mx-2">
  <a class="pt-0 pr-3" href="#">
 <img src="https://i.ibb.co/G5TN4Cm/logo.png" alt="logo" border="0">
</a>
<div class="row ml-auto">
<div class="col-md-12">
<div class="ml-auto d-flex">
    <template v-if="showHistory">
        <img src="https://www.w3schools.com/howto/img_avatar2.png"  class="profile-pic" v-if="userData.user_img">
      </template>
        <template v-else>
        <a @click="showModal('Login')" class="mr-3 mt-1 pointer small-text text-white">Login</a>
        <a @click="showModal('Signup')" class="ml-2 btn btn-sm btn-block signup-btn" >Sign up</a>
      </template>
</div>
</div>
</div>
</div></ul></nav>

  <div class="container mt-5">
    <div class="row">
  <div class="col-5">
    <!-- <img src="https://i.ibb.co/KV2VmSv/conference.png" alt="conference" border="0"> -->
  <img src="https://i.ibb.co/80W82dD/conference2.png" alt="conference" border="0" class="img-fluid">
  </div>
    <div class="col-6 pt-3 mt-3 ml-5">
      <div>
        <h3 class="conference-title">Secure, fully featured, and completely free video conferencing.</h3>
        <p class="conference-text mt-3">
          Go ahead, video chat with the whole team. In fact, invite everyone you
          know. conference.ly is a fully encrypted, 100% open source video
          conferencing solution that you can use all day, every day, for free —
          with no account needed.
        </p>
      </div>
      <div class="border mb-3 p-4 d-inline-block mt-3 hosting-section">
        <div class="d-flex mt-2">
          <div class="col-6 pr-30p" style="border-right: 1px solid #494984 !important;">
           <span class="small-text"> <span class="text-orange">Start a free trail </span>and</span>
            <span class="d-block small-text">host a meeting now.</span>
            <button type="button" class="btn btn-block mt-3 btn-lg host-btn height-50p"  @click="showModal('Public')">Host a meeting</button>
          </div>
          <div class="col-6 pl-30p mt-1">
            <p class="small-text">
              Did someone sent you meeting code? Please enter it and join the
              meeting
            </p>
            <div class="input-group join-btn">
              <input type="text" class="form-control height-50p" placeholder="Enter Code"/>
              <div class="input-group-append">
                <span class="input-group-text btn">Join</span>
              </div>
            </div>
          </div>
        </div>
        <div class="float-right mt-4">
          <p class="mb-0 conference-text">Do you want to schedule meeting later?
             <span class="text-orange cursor-pointer">Click Here</span>
          </p>
          <span class="text-grey small-text float-right">by Schedule.ly</span>
        </div>
        <HOST :modal="modal" :type="type" @dataFromHost="HostComponentData"></HOST>
      </div>
      <HISTORY v-if="showHistory"></HISTORY>
    </div>
    </div>
  </div>
  </div>
</template>

<script>
import Host from './host.vue'
import History from './history.vue'
export default {
  name: 'Index',
  components: {
    HOST: Host,
    HISTORY: History
  },
  data () {
    return {
      modal: false,
      type: 'Login',
      showHistory: false,
      userData: {}
    }
  },
  mounted () {
    if (document.cookie.length > 10) {
      var cookie = document.cookie.split(';').find(i => i.includes('token='))
      if (cookie) {
      }
    } else {
      this.showModal('Login')
    }
  },
  methods: {
    showModal (type) {
      this.modal = true
      this.type = type
    },
    closeModal () {
      this.modal = false
      this.type = ''
    },
    HostComponentData (data) {
      if (data.showHistory) {
        this.showHistory = data.showHistory
        if (data.token) this.parseJWT(data.token)
        this.userData.name = data.name
      } else if (data.hideModal) this.closeModal()
    },
    parseJWT (token) {
      var base64Url = token.split('.')[1]
      var base64 = base64Url.replace(/-/g, '+').replace(/_/g, '/')
      var jsonPayload = decodeURIComponent(atob(base64).split('').map(function (c) {
        return '%' + ('00' + c.charCodeAt(0).toString(16)).slice(-2)
      }).join(''))

      this.userData = JSON.parse(jsonPayload)
    }
  }
}
</script>
