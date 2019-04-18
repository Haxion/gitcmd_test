<template>
    <div id="content">
        <p v-show="!lists.length"><i>暂无待办事项</i></p>
        <ul>
            <li v-for="(list,index) in lists" :key="index">
                <input type="checkbox" :id="index" :value="index" v-model="selectedList">
                <label :for="index"  @click="listCheck()">
                    <span>{{index+1}}. {{list}}  {{selectedList.length}}</span>
                </label>
            </li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: 'Content_List',
      props:['lists','addTmp'],
      data(){
        return{
            selectedList:[]
        }
      },
      methods:{
        listCheck(){

        }
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

    #content ul {
        position: relative;
        margin: 5px;
        width: 100%;
    }

    #content ul li{
        position: relative;
        width: 100%;
        height: 25px;
        display: block;
    }

    #content ul li span {
        position: relative;
        width: 90%;
        padding-left: 7px;
        border-radius: 7px;
        display: inline-block;
    }

    #content ul li span:hover{
        background-color: #eeeeee;
    }

    #content p{
        margin: 20px;
        text-align: center;
    }
</style>
