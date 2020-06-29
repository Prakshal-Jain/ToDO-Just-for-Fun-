<template>
    <div>
        <div v-bind:key="to.id" v-for="to in todos">
            <EachItem v-bind:eachtodo="to" v-on:delete="$emit('delete',to.id)"/>
        </div>
    </div>
</template>

<script>
import EachItem from './EachItem'
export default {
    title: "Todos",
    components: {
        EachItem
    },
    props: ["todos"],
    methods: {

    }
}
</script>

<style lang="stylus" scoped>

</style>