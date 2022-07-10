<template>
    <div class="todo-footer">
        <label>
            <input type="checkbox" v-model="checked" @change="selectAll(checked)"/>
        </label>
            <span>已完成 {{this.showNum()}}</span> /全部{{todos.length}}
        <button class="btn btn-danger" @click="removeList">清除已完成任务</button>
    </div>
</template>

<script>
    export default {
        name: "MyFooter",
        components: {},
        props: ['todos','selectAll','removeList'],
        data() {
            return {
                checked: false
            }
        },
        methods:{
            mySelect(){
                if(this.todos.length == 0){
                    this.checked = false;
                    return;
                }
                this.checked = this.showNum() == this.todos.length?true:false;
            },
            showNum(){
                var sum = 0;
                for(var i = 0;i < this.todos.length;i++){
                    if(this.todos[i].done){
                        sum++;
                    }
                }
                return sum;
            }
        }
    };
</script>

<style scoped>
    /*footer*/
    .todo-footer {
        height: 40px;
        line-height: 40px;
        padding-left: 6px;
        margin-top: 5px;
    }

    .todo-footer label {
        display: inline-block;
        margin-right: 20px;
        cursor: pointer;
    }

    .todo-footer label input {
        position: relative;
        top: -1px;
        vertical-align: middle;
        margin-right: 5px;
    }

    .todo-footer button {
        float: right;
        margin-top: 5px;
    }
</style>