<template>
    <!--<div id="right">-->
        <div class="item">
            <span>姓名:{{list.name}}</span>
            <span>{{list.text}}</span>
            <button @click="delItem">删除</button>
        </div>
    <!--</div>-->
</template>

<script>
export default {
  name: 'Right',
  props: ['list', 'delFunction', 'index'],
  methods: {
    delItem () {
      const {list, index} = this
      if (window.confirm(`确定删除吗${list.name}`)) {
        this.delFunction(index)
      }
    }
  }
}
</script>

<style scoped>
    #right {
        float: left;
        width: 450px;
        min-height: 350px;
        padding: 30px;
        margin: 40px;
        border: solid 1px darkgrey;
    }

    .item {
        width: 100%;
        min-height: 30px;
        margin-bottom: 15px;
        border: solid 1px darkseagreen;
    }

    .item span {
        margin-right: 10px;
    }

    .item button{
        float: right;
    }

    button{
        float: right;
    }
</style>
