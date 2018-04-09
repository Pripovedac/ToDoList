<template>
    <div class="container">
        <ListItem v-for="item of itemList"
                  :task="item.task"
                  :checked="item.checked"
                  @stateChanged="changeState($event)"/>
    </div>
</template>

<script>
    import ListItem from './ListItem.vue'
    export default {
        props: ['itemList', 'filterValue'],
        components: {
            ListItem,
        },
        methods: {
            changeState: function (taskName) {
                this.$emit('stateChanged', taskName)
            },
        },

    }
</script>

<style scoped>
    .container {
        border: 1px solid black;
        height: 250px;
        width: 250px;
        margin: 0 auto;
    }
</style>