<template>
    <div id="footer">
        <input type="checkbox" v-model="allCheck">
        <span>已完成: {{totalFinish}}</span>
        <span> / </span>
        <span>全部: {{lists.length}}</span>
        <button @click="delteAllLists">清除已完成的任务</button>
    </div>
</template>

<script>
export default {
  name: 'Footer_List',
  props: {
    lists: Array,
    delteAllLists: Function,
    selectAllLists: Function
  },
  methods: {},
  computed: {
    totalFinish () {
      return this.lists.reduce((total, currentValue) => total + (currentValue.isOK ? 1 : 0), 0)
    },
    allCheck: {
      get () {
        return this.totalFinish === this.lists.length
      },
      set (checked) {
        this.selectAllLists(checked)
      }
    }
  }
}
</script>

<style scoped>
    #footer {
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

    #footer button:hover {
        background-color: lightcoral;
    }

    #footer span {
        position: relative;
        margin-top: 10px;
    }

    #footer input {
        position: relative;
        top: -1px;
    }
</style>
