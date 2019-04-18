<template>
    <div id="left">
        <p>姓名</p>
        <input type="text" v-model="name">
        <p>评论：</p>
        <textarea name="comment" v-model="text"></textarea>
        <button type="button" @click="add">提交</button>
    </div>
</template>

<script>
export default {
  name: 'Left',
  props: ['addComment'],
  data () {
    return {
      name: '',
      text: ''
    }
  },
  methods: {
    add () {
      const name = this.name.trim()
      const text = this.text.trim()
      if (!name || !text) {
        alert('请重新输入')
        return
      }
      const comment = {name, text}
      this.addComment(comment)
      this.name = ''
      this.text = ''
    }
  }
}
</script>

<style scoped>
    #left {
        float: left;
        width: 450px;
        margin: 40px;
        padding: 30px;
        border: solid 1px gray;
    }

    #left input {
        width: calc(100% - 5px);
        height: 25px;
        margin: 10px 0;
        padding-left: 5px;
    }

    #left textarea {
        width: calc(100% - 20px);
        height: 200px;
        max-width: 100%;
        padding: 10px;
        margin-top: 10px;
    }

    #left button {
        float: right;
        width: 70px;
        height: 30px;
        margin-top: 10px;
    }
</style>
