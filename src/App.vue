<template>
    <div id="app">
        <!--<router-view/>-->
        <div id="header">
            <p>Vue is good</p>
        </div>
        <div id="container">
            <left v-bind:addComment="addComment" />
            <div id="right">
                <right v-for="(list,index) in lists" v-bind:list="list" :key="index" :del-function="delComment" :index="index"/>
            </div>

        </div>
    </div>
</template>

<script>
import Left from './components/Left'
import Right from './components/Right'

export default {
  name: 'App',
  components: {
    Left,
    Right
  },
  data () {
    return {
      lists: [
        {name: 'a', text: 'this is a'},
        {name: 'b', text: 'this is b'},
        {name: 'c', text: 'this is c'}
      ]
    }
  },
  methods: {
    addComment (comment) {
      this.lists.unshift(comment)
    },
    delComment (index) {
      this.lists.splice(index, 1)
    }
  }
}
</script>

<style>
    #header {
        width: 100%;
        height: 160px;
        font-size: 50px;
        line-height: 160px;
        padding-left: 50px;
        background-color: darkgray;
    }

    #right {
        float: left;
        width: 450px;
        min-height: 350px;
        padding: 30px;
        margin: 40px;
        border: solid 1px darkgrey;
    }
</style>
