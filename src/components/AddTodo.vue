<template>
<div>
    <input type="text" name="title" v-model="added_todo" placeholder="Add todo title"/>
    <input type="button" value="Add Todo" v-on:click="add_todo()"/>
</div>
</template>

<script>
export default {
    name:"AddTodo",
    props:["numbers"],
    methods:{
        add_todo(){
            var n = this.numbers
            var constructed = {
                title:this.added_todo,
                completed:false,
                id: n+1
            }
            this.$emit('new_todo',constructed)
            this.added_todo = ""
        }
    },
    data(){
        return{
            added_todo:""
        }
    }
}
</script>