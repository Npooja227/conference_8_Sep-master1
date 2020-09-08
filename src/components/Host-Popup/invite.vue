<template>
  <div>
    <h4>Invite Guests</h4>
    <div class="mt-4 mx-2">
      <input class="form-control mt-3" placeholder="Enter Email" v-model="search" />
      <div class="mt-3 d-flex" v-for="(item,index) in filteredList" :key="index">
        <img v-if="item.image.length > 4" :src="item.image" />
        <div style="height: 40px; width: 40px; border-radius: 50px; background-color: orange;" v-else>
          <p class="text-center text-white mt-1 h4">{{item.name.charAt(0)}}</p>
        </div>
        <div class="ml-3">
          <p class="mb-0 text-capitalize">{{item.name}}</p>
          <small class="text-secondary">{{item.email}}</small>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'HostPopupInvite',
  data () {
    return {
      search: '',
      data: [{
        name: 'Pooja n',
        email: 'pooja.naraharisetty@500apps.com',
        image: ''
      }, {
        name: 'Saleem Shaik',
        email: 'saleem.shaik@500apps.com',
        image: ''
      }]
    }
  },
  computed: {
    filteredList () {
      return this.data.filter(item => {
        return item.email.toLowerCase().includes(this.search.toLowerCase())
      })
    }
  }
}
</script>

<style>
</style>
