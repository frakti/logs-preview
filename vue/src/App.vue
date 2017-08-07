<template>
  <div>
    <pre v-for="(log, idx) in logs">
      <div v-if="isNewDay(idx)">{{log.at | date}}</div>
      {{log.at | time}} {{ log.message }}
    </pre>
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
      // return false
      return !moment(prevLog.at).isSame(currentLog.at, 'day');
    }
  },
  filters: {
    time: (isoDate) => moment.utc(isoDate).format('HH:mm:ss.SSS'),
    date: (isoDate) => moment.utc(isoDate).format('DDD MMMM YYYY')
  }
}
</script>

<style lang="scss">

</style>
