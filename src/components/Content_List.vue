<template>
    <div id="content">
        <p v-show="!lists.length"><i>暂无待办事项</i></p>
        <Item_List :lists="lists" :add-tmp="addTmp"></Item_List>
    </div>
</template>

<script>
    import Item_List from './Item_List'
  export default {
    name: 'Content_List',
      props:['lists','addTmp'],
      components:{
          Item_List,
      }
  }
</script>

<style scoped>
    #content {
        position: relative;
        width: 100%;
        margin: 10px 0;
        border: solid 1px green;
    }
    #content p{
        margin: 20px;
        text-align: center;
    }
</style>
