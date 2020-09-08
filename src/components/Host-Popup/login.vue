<template>
  <div>
    <h4>{{type}}</h4>
    <form>
      <div class="mt-2" v-if="type == 'Signup'">
        <label>Name</label>
        <input type="text" class="form-control" v-model="form.name" name="name" id="name">
      </div>
      <div class="mt-2">
        <label>Email</label>
        <input type="text" class="form-control" v-model="form.email" name="email" id="email">
      </div>
      <div class="mt-2">
        <label>Password</label>
        <input type="password" class="form-control" v-model="form.password" name="password" id="password">
      </div>
      <button class="col-12 btn btn-primary mt-3 text-uppercase" @click.prevent="checkIfExists()">{{type}}</button>
    </form>
    <div class="float-right mt-2">
      <small v-if="type == 'Login'">Don't have an account? <a @click="type = 'Signup'" class="text-primary pointer">Signup</a></small>
      <small v-else-if="type == 'Signup'">Already have an account? <a @click="type = 'Login'" class="text-primary pointer">Login</a></small>
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

<style>
</style>
