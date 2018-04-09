<template>
    <div id="app">
        <img src="./assets/logo.png"> <br/>
        <List :itemList="newList" :filterValue="filter" @stateChanged="modifyOneElem($event)"/>
        <br/>
        <NewEntry @newTask="addTask($event)"/>
        <Filters @filterUsers="filterUsers($event)"/>
        <br/>
        <footer> &copy; Storyteller</footer>
    </div>
</template>

<script>
    import HelloWorld from './components/HelloWorld.vue'
    import List from './components/List.vue'
    import NewEntry from './components/NewEntry.vue'
    import Filters from './components/Filter.vue'

    export default {
        name: 'app',
        components: {
            HelloWorld,
            List,
            NewEntry,
            Filters
        },
        data() {
            return {
                newItem: "",
                filter: "all",
                mainItemList: [],
                displayList: []
            }
        },
        methods: {
            addTask(newTask) {
                let newItem = {task: newTask, checked: false}
                this.mainItemList.push(newItem)
            },
            filterUsers(radioFilter) {
                this.filter = radioFilter
                if (radioFilter == 'all') {
                    this.displayList = [...this.mainItemList]
                }
                else {
                    this.displayList = this.mainItemList.filter(item => item.checked == radioFilter)
                }
            },
            modifyOneElem(stateSwapper) {
                let modifiedElement = this.mainItemList.find(item => item.task == stateSwapper)
                let modifiedIndex = this.mainItemList.indexOf(modifiedElement)
                let alteredListOne = this.mainItemList.splice(0, modifiedIndex)
                alteredListOne.push({task: modifiedElement.task, checked: !modifiedElement.checked})
                let alteredListTwo = this.mainItemList.splice(modifiedIndex)
                this.mainItemList = alteredListOne.concat(alteredListTwo)
            }

        },
        computed: {
            newList: function () {
                // Computed props change everytime some of its dependencies changes
                // in this case mainItemList.
                // It's just like any other function, except it's more optimal, because
                // it won't calucalte the result over and over again if parameters
                // are not changed.
                if (this.filter == 'all') {
                    return [...this.mainItemList]
                }
                else {
                    return this.mainItemList.filter(item => item.checked == this.filter)
                }
            }
        }
    }
</script>

<style>
    #app {
        font-family: 'Avenir', Helvetica, Arial, sans-serif;
        -webkit-font-smoothing: antialiased;
        -moz-osx-font-smoothing: grayscale;
        text-align: center;
        color: #2c3e50;
        margin-top: 60px;
    }
</style>
