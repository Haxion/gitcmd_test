<template>
    <div id="search-top">
        <div id="search-bar">
            <input placeholder="输入要查询的用户名" @keydown.enter="searchClick" v-model="msg">
            <button type="button" @click="searchClick">查询</button>
        </div>
    </div>
</template>

<script>
import PubSub from 'pubsub-js'
export default {
  name: 'SearchTop',
  data () {
    return {
      msg: ''
    }
  },
  methods: {
    searchClick () {
      const msg = this.msg.trim()
      if (msg) {
        PubSub.publish('userList', msg)
        this.msg = ''
      }
    }
  }
}
</script>

<style scoped>
    #search-top {
        position: relative;
        height: 100px;
        padding-top: 50px;
        margin-bottom: 30px;
        background: lightgray;
    }

    #search-top #search-bar {
        position: relative;
        width: 400px;
        margin: 0 auto;
    }

    #search-top #search-bar input {
        position: relative;
        width: 300px;
        height: 30px;
        padding-left: 4px;
        line-height: 30px;
        outline: none;
    }

    #search-top #search-bar button {
        position: relative;
        width: 40px;
        height: 32px;
    }
</style>
