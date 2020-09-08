<template>
  <div
    class="border mt-5 mb-5 p-4 d-inline-block col-12"
    style="border-color:#5934ab !important;background-color: #391f73;"
  >
    <b-tabs content-class="mt-3">
      <b-tab title="Recent Meetings" active>
        <div
          :class="index != recent.length-1?'border-bottom':''"
          v-for="(item,index) in recent"
          :key="index"
        >
          <div class="d-flex mb-2 text-capitalize" :class="index>0?' mt-2': ''">
            <div class="col-5 text-left">
              <p class="mb-0" style="color:#aaa">{{item.name}}</p>
              <small class="text-muted">{{item.total_time}}</small>
            </div>
            <div class="col-4 text-left">
              <p class="mb-0" style="color:#aaa">{{item.date}}</p>
              <small class="text-muted">{{item.time}}</small>
            </div>
            <div class="col-3">
              <p class="mt-2 pt-1" style="color:orange">Connect</p>
            </div>
          </div>
        </div>
      </b-tab>
      <b-tab title="Upcoming Meetings">
        <div
          :class="index != upcoming.length-1?'border-bottom':''"
          v-for="(item,index) in upcoming"
          :key="index"
        >
          <div class="d-flex mb-2 text-capitalize" :class="index>0?' mt-2': ''">
            <div class="col-5 text-left">
              <p class="mb-0" style="color:#aaa">{{item.name}}</p>
              <small>
                <span class="text-muted" style="color:#aaa">Organizer: {{item.organizer}}</span>
              </small>
            </div>
            <div class="col-4 text-left">
              <p class="mb-0" style="color:#aaa">{{item.date}}</p>
              <small class="text-muted">{{item.time}}</small>
            </div>
            <div class="col-3">
              <p class="mt-2 pt-1" style="color:orange">Join</p>
            </div>
          </div>
        </div>
      </b-tab>
    </b-tabs>
  </div>
</template>

<script>
export default {
  name: 'History',
  data () {
    return {
      recent: [
        {
          name: 'PM Scrum',
          total_time: '01:03:00',
          date: '26 Jun',
          time: '13:00 - 14:00'
        },
        {
          name: 'frontend-team',
          total_time: '00:25:00',
          date: '27 Jun',
          time: '14:00 - 15:00'
        },
        {
          name: 'backend-team',
          total_time: '00:50:00',
          date: '28 Jun',
          time: '12:00 - 13:00'
        }
      ],
      upcoming: [
        {
          name: 'Design Sprint',
          organizer: 'you',
          date: '26 Jun',
          time: '13:00 - 14:00'
        },
        {
          name: 'Marketing Updates',
          organizer: 'Satya',
          date: '27 Jun',
          time: '14:00 - 15:00'
        },
        {
          name: 'Marketing updates',
          organizer: 'Natalia',
          date: '28 Jun',
          time: '12:00 - 13:00'
        }
      ]
    }
  }
}
</script>

<style>
.nav-tabs {
  border-bottom: 1px solid #5934ab;
}
.nav-tabs .nav-link.active {
  border: none;
  border-bottom: 3px solid #fff;
  color: #fff !important;
  background: none;
}
.nav-link {
  color: #aaa !important;
}
.border-bottom {
  border-bottom: 1px solid rgb(77, 59, 115) !important;
}
</style>
