<template>
    <div class="container">
        <ListItem v-for="item of newList"
                  :task="item.task"
                  :checked="item.checked"
                  @stateChanged="changeState($event)"/>
    </div>
</template>

<script>
    import ListItem from './ListItem.vue'

    export default {
        props: ['newItem', 'filterValue'],
        components: {
            ListItem,
        },
        data() {
            return {
                numOfRows: 10,
                numOfCols: 30,
                itemList: [],
            }
        },
        methods: {
            changeState: function (taskName) {
                let modifiedItem = this.itemList.find(item => item.task == taskName)
                modifiedItem.checked = !modifiedItem.checked
            },
        },
        computed: {
            newList: function () {
                if (this.filterValue == 'all') {
                    return [...this.itemList]
                }
                else {
                    return this.itemList.filter(item => item.checked == this.filterValue)
                }
            }
        },
        watch: {
            newItem: function (newValue) {
                let newItem = {task: newValue, checked: false}
                this.itemList.push(newItem)
                this.displayedList = [...this.itemList]
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