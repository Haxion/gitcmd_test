<template>
    <div id="search-result">
        <h3>搜寻结果</h3>
        <div id="search-content">
            <!--<div class="search-item" v-for="(item, index) in items" :key="index">-->
                <!--<img src="../../static/bg.png" alt="">-->
                <!--<a href="">名字</a>-->
            <!--</div>-->
            <div class="search-item" v-for="(user, index) in usersInfo" :key="index">
                <img :src="user.src" alt="头像">
                <a :href="user.href">{{user.name}}</a>
            </div>
        </div>
    </div>
</template>

<script>
import PubSub from 'pubsub-js'
import axios from 'axios'
export default {
  name: 'SearchResult',
  data () {
    return {
      usersInfo: null
    }
  },
  mounted () {
    PubSub.subscribe('userList', (msg, data) => {
      const useURL = `https://api.github.com/search/users?q=${data}`
      this.usersInfo = null
      axios.get(useURL).then((response) => {
        // 成功获取数据
        const result = response.data
        const resultItem = result.items
        const resultAry = []
        for (let i = 0; i < 10; i++) {
          let obj = {}
          obj.href = resultItem[i].html_url
          obj.src = resultItem[i].avatar_url
          obj.name = resultItem[i].login
          resultAry.push(obj)
        }
        this.usersInfo = resultAry
        console.log(this.usersInfo)
      }).catch(error => {
        console.log(error)
      })
    })
  }
}
</script>

<style scoped>
    #search-result {
        position: relative;
        width: 100%;
        padding: 10px;
        border: solid 1px gold;
        text-align: center;
    }

    #search-result :after {
        content: '';
        clear: both;
        display: block;
    }

    .search-item {
        float: left;
        width: 140px;
        height: 160px;
        margin: 20px 10px;
        border: solid 1px darkcyan;
    }

    .search-item img {
        width: 140px;
        height: 160px;
    }
</style>
