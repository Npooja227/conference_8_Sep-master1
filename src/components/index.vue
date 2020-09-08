<template>
  <div class="landing-bg" :style="showHistory?'height: auto;':'height: 100%'">
    <div v-if="showHistory" class="mr-5 float-right mt-3 text-primary">
      <!--<img src="https://www.w3schools.com/howto/img_avatar2.png" class="profile-pic" v-if="userData.user_img">-->
      <img :src="userData.user_img" class="profile-pic" v-if="userData.user_img">
      <p :data-letters="userData.name.charAt(0)" v-else></p>
    </div>
    <div class="mr-5 float-right mt-3 text-primary" v-else>
      <a @click="showModal('Login')" class="pointer text-white">Login</a>
      <a @click="showModal('Signup')" class="ml-3 btn btn-sm pointer text-white" style="background-color: orange;">Signup</a>
    </div>
<div class="col-6 pt-5 pl-5">
  <div class="header-text">
    <h1 class="header-text-title">Secure, fully featured, and completely free video conferencing</h1>
    <p class="header-text-description">
      Go ahead, video chat with the whole team. In fact, invite everyone you
      know. conference.ly is a fully encrypted, 100% open source video
      conferencing solution that you can use all day, every day, for free —
      with no account needed.
    </p>
  </div>
  <div class="border mt-1 p-4 d-inline-block" style="border-color: #555598 !important;background-color: #261252;">
    <div class="d-flex">
      <div class="col-5" style="border-right: 1px solid #294765 !important;">
        <span style="color:orange">Start a free trail and</span>
        <br />
        <span>host a meeting now.</span>
        <button type="button" class="btn mt-3 btn-lg mr-2" style="background-color: #6f2bff;color: white;" @click="showModal('Public')">Host a meeting</button>
      </div>
      <div class="col-7">
        <p>
          Did someone sent you meeting code? Please enter it and join the
          meeting
        </p>
        <div class="input-group">
          <input type="text" class="form-control" placeholder="Enter Code" />
          <div class="input-group-append">
            <span class="input-group-text">Join</span>
          </div>
        </div>
      </div>
    </div>
    <div class="float-right mt-4">
      <p class="mb-0">
        Do you want to schedule meeting later?
        <span style="color:orange">Click Here</span>
      </p>
      <small class="text-secondary float-right">By Schedule.ly</small>
    </div>
    <HOST :modal="modal" :type="type" @dataFromHost="HostComponentData"></HOST>
  </div>
  <HISTORY v-if="showHistory"></HISTORY>
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
<style>
  .header .header-text {
    display: flex;
    flex-direction: column;
    margin-top: 200px;
    margin-bottom: 0px;
    max-width: calc(100% - 40px);
    width: 50%;
    z-index: 2;
    max-width: 620px;
  }

  .header .header-text-title {
    color: #fff;
    font-size: 3rem;
    font-weight: 500;
    line-height: 1.18;
    margin-bottom: 16px;
    opacity: 1;
  }

  .header .header-text-description {
    display: inherit;
    color: #fff;
    font-size: 1rem;
    font-weight: 400;
    line-height: 24px;
    margin-bottom: 40px;
    align-self: inherit;
  }

  .landing-bg {
    /* background-image: url(https://1.bp.blogspot.com/-YLDLu1GApmQ/Tm-cKFIKE1I/AAAAAAAAEvQ/bp1zLkKJ6Cg/w1200-h630-p-k-no-nu/Purple+solid+color+backgrounds+1.png) !important; */
    background-image: url(https://meeting.500apps.org/images/landing-bg.svg) !important;
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
  }

  .profile-pic {
    width: 50px;
    height: 50px;
    border-radius: 50%;
  }

  [data-letters]:before {
    content: attr(data-letters);
    display: inline-block;
    font-size: 1em;
    width: 50px;
    height: 50px;
    line-height: 3em;
    text-align: center;
    border-radius: 50%;
    background: plum;
    vertical-align: middle;
    margin-right: 1em;
    color: white;
    text-transform: capitalize;
  }
</style>
