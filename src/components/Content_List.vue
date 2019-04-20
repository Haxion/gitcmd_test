<template>
    <div id="content">
        <p v-show="!lists.length"><i>暂无待办事项</i></p>
        <ul>
            <ItemList v-for="(list,index) in lists" :key="index" :list="list" :index="index" :delList="delList"></ItemList>
        </ul>
    </div>
</template>

<script>
import ItemList from './Item_List'
export default {
  name: 'Content_List',
  props: ['lists', 'delList'],
  components: {
    ItemList
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
    #content ul {
        position: relative;
        margin: 5px;
        width: 100%;
    }

</style>
