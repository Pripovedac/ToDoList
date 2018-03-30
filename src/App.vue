<template>
    <div id="app">
        <img src="./assets/logo.png"> <br/>
        <List :newItem="newItem" :filterValue="filter"/>
        <br/>
        <NewEntry @newTask="addTask($event)"/>
        <Filters @filterUsers="filterUsers($event)"/>
        <br/>
        <footer> &copy Storyteller</footer>
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
            }
        },
        methods: {
            addTask(newTask) {
                this.newItem = newTask
            },
            filterUsers(radioFilter) {
                this.filter = radioFilter
            }
        },
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
