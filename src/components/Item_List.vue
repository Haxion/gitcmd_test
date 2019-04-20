<template>
    <li @mouseenter="handleEnter(true)" @mouseleave="handleEnter(false)">
        <label>
            <input type="checkbox" v-model="list.isOK">
            <span :style="{background:bgColor}">{{index+1}}. {{list.text}}</span>
            <button v-show="isShow" @click="delItem">删除</button>
        </label>
    </li>
</template>

<script>
export default {
  name: 'Item_List',
  props: ['list', 'index', 'delList'],
  data () {
    return {
      bgColor: 'white',
      isShow: false
    }
  },
  methods: {
    handleEnter (isEnter) {
      if (isEnter) {
        this.bgColor = '#eeeeee'
        this.isShow = true
      } else {
        this.bgColor = 'white'
        this.isShow = false
      }
    },
    delItem () {
      const {list, index} = this
      if (window.confirm(`确认删除 ${list.text} 吗`)) {
        this.delList(index)
      }
    }
  }
}
</script>

<style scoped>

    li {
        position: relative;
        width: 100%;
        height: 30px;
        display: block;
    }

    li input{
        position: relative;
        top: -2px;
    }

    li span {
        position: relative;
        width: 90%;
        height: 30px;
        padding-left: 7px;
        line-height: 30px;
        border-radius: 7px;
        display: inline-block;
    }

    li span:hover {
        background-color: #eeeeee;
    }

    li button {
        position: absolute;
        width: 40px;
        right: 20px;
        margin: 5px 0;
    }

</style>
