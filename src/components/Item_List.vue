<template>
    <div>
        <ul>
            <li v-for="(list,index) in lists" :key="index">
                <input type="checkbox" :id="index" :value="index" v-model="selectedList">
                <label :for="index"  @click="listCheck()">
                    <span>{{index+1}}. {{list}}  {{selectedList.length}}</span>
                    <button>删除</button>
                </label>
            </li>
        </ul>
    </div>
</template>

<script>
  export default {
    name: 'Item_List',
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
    ul {
        position: relative;
        margin: 5px;
        width: 100%;
    }

    ul li{
        position: relative;
        width: 100%;
        height: 25px;
        display: block;
    }

    ul li span {
        position: relative;
        width: 90%;
        padding-left: 7px;
        border-radius: 7px;
        display: inline-block;
    }

    ul li span:hover{
        background-color: #eeeeee;
    }

    ul li button{
        position: absolute;
        right: 20px;
        display: none;
    }

</style>
