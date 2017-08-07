<template>
  <div>
    <pre v-for="log in logs">
      {{log.at}} {{ log.message }}
    </pre>
  </div>
</template>

<script>
import logs from '../../example-logs.json'

export default {
  name: 'app',
  data () {
    return {
      logs
    }
  }
}
</script>

<style lang="scss">

</style>
