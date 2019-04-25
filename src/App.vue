<template>
    <div id="app">
        <!--<router-view/>-->
        <search-top/>
        <search-result/>
    </div>
</template>

<script>

import PubSub from 'pubsub-js'
import SearchTop from './components/SearchTop'
import SearchResult from './components/SearchResult'
export default {
  name: 'App',
  components: {
      SearchTop,
      SearchResult
  },
  data () {
    return {

    }
  },
  methods: {

  },
  mounted () {
    PubSub.subscribe('delList', (msg, index) => {
      this.delList(index)
    })
  }
}
</script>

<style>

</style>
