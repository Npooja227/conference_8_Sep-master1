<template>
  <div class="p-4 mx-3 host-meeting">
    <h4 class="border-bottom pb-3 font-weight-normal mt-1">Host a meeting</h4>
    <div class="row">
      <div class="col-md-7">
    <form class="mt-3 fw-500 font-14px">
      <label class="mb-2 bolder-text">Select Room Type</label>
      <div class="mb-2 mt-1 ">
        <input type="radio" id="room_type_public"  name="room_type" v-model="room_type" value="public" />
        <label for="room_type_public">Public Room</label>
        <input id="room_type_private" type="radio" name="room_type" v-model="room_type" value="private"  />
        <label for="room_type_private" class="ml-4">Private Room</label>
      </div>
    </form>
    <div>
      <img src="https://www.w3schools.com/html/img_girl.jpg" :alt="member" class="host-avatar" />
      <span>
        <small>
          <span class="text-muted">by</span>
          <span class="text-capitalized">{{ member }}</span>
        </small>
      </span>
    </div>
    <div class="input-group my-3">
      <div class="input-group-prepend">
        <span class="input-group-text text-muted border-right-0">{{ url }}</span>
      </div>
      <input type="text" class="form-control border-left-0" :disabled="room_type == 'public'" v-model="username" />
    </div>
    <div v-if="room_type == 'private'" class="d-flex">
      <img src="https://img.icons8.com/metro/26/000000/lock.png"  class="lock-icon mr-2 mt-1" />
      <p class="text-muted secure-meeting-text mb-1">Secure the meeting</p>
      <div class="ml-2 custom-control custom-switch" style="padding-top: 0.15rem;">
        <input type="checkbox" class="custom-control-input" id="customSwitch1" v-model="secure_meeting" />
        <label class="custom-control-label" for="customSwitch1"></label>
      </div>
      <input type="text"  v-if="secure_meeting" class="form-control col-5 ml-auto enter-code-input" placeholder="Enter your code" />
    </div>
    <div>
      <p class="text-grey-light small-text mt-2 mb-2">
        Conference.ly is hosted in multiple locations. We detected that your
        nearest location to our conference servers is "US1 - New York".
        <a class="text-primary">Change Location.</a>
      </p>
    </div>
    <div class="my-3" style="display: grid">
      <small class="text-primary ml-auto mb-2 pointer fw-500" @click="showInvite = true">+ Invite Guests</small>
      <HOST :modal="showInvite" type="Invite"></HOST>
      <button class="btn btn-primary" @click="showJitsi()">Create Meeting</button>
    </div>
      </div>
    <div class="col-md-5 mt-4">
    <img src="https://i.ibb.co/D898ws6/host-meeting.png" alt="host-meeting" class="img-fluid"  border="0">
    </div>
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
