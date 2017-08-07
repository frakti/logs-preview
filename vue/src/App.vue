<template>
  <div>
    <pre v-for="log in logs">
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
  filters: {
    time: (isoDate) => {
      // return "a";
      return moment.utc(isoDate).format('HH:mm:ss.SSS')
    }
  }
}
</script>

<style lang="scss">

</style>
