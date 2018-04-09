<template>
    <div class="entry">
        <input type="checkbox"
               :checked="checked"
               @click="changeState($event)">
        <span>{{task}}</span>
    </div>
</template>

<script>
    export default {
        props: ['task', 'checked'],
        data() {
            return {}
        },
        methods: {
            changeState(event) {
                // I know I'm not using event in this method.
                this.$emit("stateChanged", this.task)
                console.log('ListItem: ', this.task)
            }
        }
    }
</script>

<style scoped>
    .entry {
        display: flex;
    }
</style>