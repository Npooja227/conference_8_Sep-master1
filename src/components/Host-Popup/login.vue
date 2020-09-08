<template>
<div class="row">
  <div class="col-md-5 left-sec pl-7 pr-7 pb-4 login-bg">
<!-- <img src="https://i.ibb.co/SRksKrG/Screenshot-3.png" alt="Screenshot-3" border="0"> -->
    <img src="https://i.ibb.co/80W82dD/conference2.png" alt="conference" border="0" class="img-fluid">
  </div>
  <div class="col-md-7 pt-3 pl-4 pb-4 pr-md-0 pr-8 text-center align-self-center">
    <div class="p-4 signup-content">
      <h4 class="mb-4 text-left pt-3">{{type}}</h4>
      <form>
        <div class="form-group login-form mt-2 text-left fw-500" v-if="type == 'Signup'">
          <!-- <label><small> Name </small> </label> -->
          <span class="fal fa-user form-control-feedback"></span>
          <input type="text" class="form-control" v-model="form.name" name="name" id="name" placeholder="Name">
        </div>
        <div class="mt-2 form-group login-form text-left fw-500">
          <!-- <label><small> Email</small></label> -->
          <span class="fal fa-envelope form-control-feedback"></span>
          <input type="text" class="form-control" v-model="form.email" name="email" id="email" placeholder="Email">
        </div>
        <div class="mt-2 text-left fw-500 form-group login-form">
          <!-- <label><small>Password</small></label> -->
            <span class="fal fa-lock-alt form-control-feedback"></span>
          <input type="password" class="form-control" v-model="form.password" name="password" id="password" placeholder="Password">
        </div>
        <button class="col-12 btn btn-primary mt-2 text-uppercase" @click.prevent="checkIfExists()">{{type}}</button>
      </form>
      <div class="float-right mt-2 mb-3">
        <div v-if="type == 'Login'">Don't have an account? <a @click="type = 'Signup'" class="ml-1 fw-400 pointer text-purple">Sign up</a></div>
        <div v-else-if="type == 'Signup'">Already have an account? <a @click="type = 'Login'" class="ml-1 fw-400 pointer text-purple">Login</a></div>
      </div>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HostPopupIndex',
  props: {
    type: String
  },
  data () {
    return {
      form: {}
    }
  },
  methods: {
    checkIfExists () {
      if (this.type === 'Login') this.login()
      else this.signup()
    },
    login () {
      this.$emit('messageFromChild', {modal: false, showHistory: true, token: '', name: 'Conference.ly'})
    },
    signup () {
      this.login()
    }
  }
}
</script>
