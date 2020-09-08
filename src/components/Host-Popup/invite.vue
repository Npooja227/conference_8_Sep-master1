<template>
  <div class="p-4">
    <h4>Invite Guests</h4>
    <div class="mt-4 mx-2">
      <input class="form-control mt-3" placeholder="Enter Email" v-model="search" />
   <div class="my-2 pt-1">
      <div class="mt-3 d-flex" v-for="(item,index) in filteredList" :key="index">
        <img v-if="item.image.length > 4" :src="item.image" />
        <div class="invite-user" v-else>
          <p class="text-center text-white mt-1 h4">{{item.name.charAt(0)}}</p>
        </div>
        <div class="ml-3">
          <p class="mb-0 text-capitalize">{{item.name}}</p>
          <div class="font-14px mt-n1 text-grey-light">{{item.email}}</div>
        </div>
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
