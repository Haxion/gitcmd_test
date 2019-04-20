<template>
    <div id="app">
        <!--<router-view/>-->
        <div id="box">
            <HeaderList :addList="addList"/>
            <ContentList :lists="lists" :delList="delList"/>
            <FooterList :lists="lists" :selectAllLists="selectAllLists" :delteAllLists="delteAllLists"/>
        </div>

    </div>
</template>

<script>
import HeaderList from './components/Header_List'
import ContentList from './components/Content_List'
import FooterList from './components/Footer_List'

export default {
  name: 'App',
  components: {
    HeaderList,
    ContentList,
    FooterList
  },
  data () {
    return {
      todo_message: '',
      lists: JSON.parse(window.localStorage.getItem('lists') || '[]')
    }
  },
  methods: {
    addList (todoMessage) {
      this.lists.push(todoMessage)
    },
    delList (todoIndex) {
      this.lists.splice(todoIndex, 1)
    },
    selectAllLists (status) {
      this.lists.forEach(list => { list.isOK = status })
    },
    delteAllLists () {
      this.lists = this.lists.filter(list => !list.isOK)
    }
  },
  watch: {
    lists: {
      handler: function (value) {
        // 将 todo 最新值的 JSON 数据，保存到 localStorage 中
        window.localStorage.setItem('lists', JSON.stringify(value))
      }
    }
  }
}
</script>

<style>

</style>
