<template>
  <div>
    <h3 class="text-muted border-bottom pb-4">Host a meeting</h3>
    <form class="mt-4">
      <label>Select Room Type</label>
      <div>
        <input type="radio" name="room_type" v-model="room_type" value="public" />
        <label>Public Room</label>
        <input type="radio" name="room_type" v-model="room_type" value="private" class="ml-4" />
        <label>Private Room</label>
      </div>
    </form>
    <div>
      <img src="https://www.w3schools.com/html/img_girl.jpg" :alt="member" style="border-radius: 50%; height: 35px; width: 35px;" />
      <span>
        <small>
          <span class="text-muted">by</span>
          <span class="text-capitalized">{{ member }}</span>
        </small>
      </span>
    </div>
    <div class="input-group my-3">
      <div class="input-group-prepend">
        <span class="input-group-text">{{ url }}</span>
      </div>
      <input type="text" class="form-control" :disabled="room_type == 'public'" v-model="username" />
    </div>
    <div v-if="room_type == 'private'" class="d-flex">
      <img src="https://img.icons8.com/metro/26/000000/lock.png" style="height: 17px;" class="mr-2 mt-1" />
      <p class="text-muted">Secure the meeting</p>
      <div class="ml-2 custom-control custom-switch" style="padding-top: 0.15rem;">
        <input type="checkbox" class="custom-control-input" id="customSwitch1" v-model="secure_meeting" />
        <label class="custom-control-label" for="customSwitch1"></label>
      </div>
      <input type="text"  v-if="secure_meeting" class="form-control col-4 ml-auto" placeholder="Enter your code" />
    </div>
    <div>
      <small class="text-secondary">
        Conference.ly is hosted in multiple locations. We detected that your
        nearest location to our conference servers is "US1 - Newyork".
        <a class="text-primary">Change Location.</a>
      </small>
    </div>
    <div class="my-3" style="display: grid">
      <small class="text-primary ml-auto mb-2 pointer" @click="showInvite = true">+ Invite Guests</small>
      <HOST :modal="showInvite" type="Invite"></HOST>
      <button class="btn btn-primary" @click="showJitsi()">Create Meeting</button>
    </div>
  </div>
</template>

<script>
import Host from '../host.vue'
export default {
  name: 'Public',
  components: {
    HOST: Host
  },
  data () {
    return {
      room_type: 'public',
      member: 'You',
      url: 'https://our.conference.ly/',
      username: '',
      secure_meeting: false,
      showInvite: false,
      jitsiBlock: false
    }
  },
  methods: {
    showJitsi () {
      if (this.username) {
      }
    }
  }
}
</script>

<style></style>
