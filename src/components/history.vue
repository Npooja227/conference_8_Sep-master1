<template>
  <div
    class="border mt-4 mb-5 pt-3 d-inline-block col-12 px-0 meeting-card"
    style="border-color:#5934ab !important;background-color: #391f73;"
  >
    <b-tabs>
      <b-tab title="Recent Meetings" active class="mt-1">
        <div class="meeting-table px-2r" v-for="(item,index) in recent" :key="index">
          <div class=" d-flex text-capitalize pt-2 fw-500"  :class="index != recent.length-1?'border-bottom':''">
            <div class="col-5 text-left pl-0">
              <p class="mb-0 meeting-table-text">{{item.name}}</p>
              <small class="text-muted">{{item.total_time}}</small>
            </div>
            <div class="col-4 text-left">
              <p class="mb-0 meeting-table-text">{{item.date}}</p>
              <small class="text-muted">{{item.time}}</small>
            </div>
            <div class="col-3 text-right">
              <p class="cursor-pointer font-14px mb-4 mt-1 pt-1 text-orange">Connect</p>
            </div>
          </div>
        </div>
      </b-tab>
      <b-tab title="Upcoming Meetings"  class="mt-1">
        <div class="meeting-table px-2r" v-for="(item,index) in upcoming" :key="index">
          <div class="d-flex pt-2 text-capitalize fw-500"   :class="index != upcoming.length-1?'border-bottom':''">
            <div class="col-5 text-left pl-0">
              <p class="mb-0 meeting-table-text">{{item.name}}</p>
              <small>
                <span class="text-muted meeting-table-text">Organizer: {{item.organizer}}</span>
              </small>
            </div>
            <div class="col-4 text-left">
              <p class="mb-0 meeting-table-text">{{item.date}}</p>
              <small class="text-muted">{{item.time}}</small>
            </div>
            <div class="col-3 text-right">
              <p class="cursor-pointer font-14px mb-4 mt-1 pt-1 text-orange">Join</p>
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
