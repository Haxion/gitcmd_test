<template>
    <div id="footer">
        <span>已完成: 0</span>
        <span> / </span>
        <span>全部: {{lists.length}}</span>
        <button @click="listDelete">清除已完成的任务</button>
    </div>
</template>

<script>
  export default {
    name: 'Footer_List',
      props:['lists','delTmp'],
      methods:{
        listDelete(){
            this.delTmp();
        }
      }
  }
</script>

<style scoped>
    #footer{
        position: relative;
        width: 100%;
    }

    #footer button {
        position: absolute;
        height: 30px;
        padding: 0 5px;
        right: 0;
        border-radius: 4px;
        outline-style: none;
    }

    #footer button:hover{
        background-color: lightcoral;
    }

    #footer span{
        position: relative;
        margin-top: 10px;
    }
</style>
