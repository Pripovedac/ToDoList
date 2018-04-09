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
                let modifiedItem = this.itemList.find(item => item.task == taskName)
                modifiedItem.checked = !modifiedItem.checked
                console.log('ChangeState in List:' , taskName)
                this.$emit('stateChanged')
            },
        },
        // computed: {
        //     newList: function () {
        //         // Computed props change everytime some of its dependencies changes
        //         // in this case filter, or itemList.
        //         // It's just like any other function, except it's more optimal, because
        //         // it won't calucalte the result over and over again if parameters
        //         // are not changed.
        //         console.log('Filter changed.')
        //         if (this.filterValue == 'all') {
        //             return  [...this.itemList]
        //         }
        //         else {
        //             return this.itemList.filter(item => item.checked == this.filterValue)
        //         }
        //     }
        //}
        // watch: {
        //     newItem: function (newValue) {
        //         let newItem = {task: newValue, checked: false}
        //         this.itemList.push(newItem)
        //         this.displayedList = [...this.itemList]
        //     },
        // },
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