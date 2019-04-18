<template>
    <div id="header">
        <input type="text" placeholder="在此输入待办事项" v-model="msg" @keydown.enter="todo_submit">
    </div>
</template>

<script>
    export default {
        name: 'Header_List',
        props:['addList'],
        data(){
            return{
                msg:'',
            }
        },
        methods:{
            todo_submit(){
                this.addList(this.msg)
                this.msg = ''
            }
        }
    }
</script>

<style scoped>
    #header input {
        position: relative;
        width: calc(100% - 5px);
        height: 30px;
        padding-left: 5px;
        outline: none;
    }
</style>
