<template>
    <div>
        <label v-bind:class="{'is_complete':eachtodo.completed}"><input type="checkbox" v-on:change="markComplete">{{eachtodo.title}}<button v-on:click="$emit('delete',eachtodo.id)" style="margin-left:5px;">Delete</button></label>
    </div>
</template>

<script>
export default {
    name: "EachItem",
    props: ["eachtodo"],
    methods: {
        markComplete(){
            this.eachtodo.completed = !this.eachtodo.completed
        }
    }
}
</script>

<style scoped>
    .is_complete{
        text-decoration: line-through;
    }
</style>