<template>
    <div id="app">
        <!--<router-view/>-->
        <div id="box">
            <header_-list :addList="addList"/>
            <content_-list :lists="lists" :addTmp="addTmp"/>
            <footer_-list :lists="lists" :delTmp="delTmp"/>
        </div>

    </div>
</template>

<script>
import Header_List from './components/Header_List'
import Content_List from './components/Content_List'
import Footer_List from './components/Footer_List'

export default {
  name: 'App',
  components: {
    Header_List,
      Content_List,
      Footer_List,
  },
  data () {
    return {
        todo_message:'',
      lists: [],
        tmpAry:[]
    }
  },
  methods: {
      addList(todo_message){
          todo_message = todo_message.trim();
          if (todo_message){
              this.lists.push(todo_message);
              // console.log(this.lists)
          } else {
              alert('输入内容不能为空！')
          }
      },
      addTmp(tmpAry){
          this.tmpAry = tmpAry;
          console.log(this.tmpAry)
          console.log(this)
      },
      delTmp(){
          if (this.tmpAry.length===0){
              return
          }
          for (let i=0;i<this.tmpAry.length;i++){
              this.lists.splice(this.tmpAry[i],1)
          }
      }
  }
}
</script>

<style>

</style>
