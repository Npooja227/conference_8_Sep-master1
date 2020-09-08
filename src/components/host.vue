<template>
  <div>
    <b-modal id="modal" ref="modal" hide-header hide-footer no-close-on-backdrop no-close-on-esc>
      <button type="button" aria-label="Close" class="close" @click="hide()">×</button>
      <template>
        <LOGIN v-if="type == 'Login' || type == 'Signup'" :type="type" @messageFromChild="ChildComponentData"></LOGIN>
        <INVITE v-else-if="type == 'Invite'"></INVITE>
        <PUBLIC v-else-if="type == 'Public'"></PUBLIC>
        <PRIVATE v-else-if="type == 'Private'"></PRIVATE>
      </template>
    </b-modal>
  </div>
</template>

<script>
import Login from './Host-Popup/login.vue'
import Invite from './Host-Popup/invite.vue'
import Public from './Host-Popup/public.vue'
import Private from './Host-Popup/private.vue'
export default {
  name: 'Host',
  props: {
    modal: Boolean,
    type: String
  },
  components: {
    'LOGIN': Login,
    'INVITE': Invite,
    'PUBLIC': Public,
    'PRIVATE': Private
  },
  methods: {
    show () {
      this.$refs.modal.show()
    },
    hide () {
      this.$emit('dataFromHost', {hideModal: true})
      this.$refs.modal.hide()
    },
    ChildComponentData (data) {
      if (!data.modal) this.hide()
      if (data.showHistory) this.$emit('dataFromHost', {showHistory: data.showHistory, token: data.token, name: data.name})
    }
  },
  watch: {
    modal: function (val) {
      if (val) this.show()
      else this.hide()
    },
    type: function (val) {
      if (this.modal) this.show()
    }
  }
}
</script>

<style>
</style>
