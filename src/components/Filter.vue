<template>
    <div>
        <br/>
        <label>Show everything <input type="radio" name="toDo" checked="checked"
                                      @click="filterUsers('all')"/></label>
        <label>Show done <input type="radio" name="toDo" @click="filterUsers(true)"/></label>
        <label>Show to be done <input type="radio" name="toDo" @click="filterUsers(false)"/></label>
    </div>
</template>

<script>
    export default {
        data() {
            return {};
        },
        methods: {
            filterUsers(event) {
                this.$emit('filterUsers', event)
            }
        }
    }
</script>

<style scoped>

</style>