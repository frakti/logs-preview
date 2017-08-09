<template>
  <div>
    <template v-for="(log, idx) in logs">

      <div v-if="isNewDay(idx)" class="day-indicator">{{log.at | date}}</div>
      <pre>{{log.at | time}} {{ log.message }}</pre>
    </template>
  </div>
</template>

<script>
import logs from '../../example-logs.json'
import moment from 'moment'

export default {
  name: 'app',
  data () {
    return {
      logs
    }
  },
  methods: {
    isNewDay: function (index) {
      if (index === 0) {
        return true;
      }

      const prevLog = this.logs[index - 1]
      const currentLog = this.logs[index]

      return !moment(prevLog.at).isSame(currentLog.at, 'day');
    }
  },
  filters: {
    time: (isoDate) => moment.utc(isoDate).format('HH:mm:ss.SSS'),
    date: (isoDate) => moment.utc(isoDate).format('D MMMM YYYY')
  }
}
</script>

<style lang="scss">
.day-indicator {
  display: flex;
  flex-direction: row;

  &:before, &:after {
    content: "";
    flex: 1 1;
    border-bottom: 1px solid #000;
    margin: auto;
  }
}
</style>
