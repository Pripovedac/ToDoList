<template>
    <div>
        <label> <input type="text" v-model="task" ref="inputField" @keyup.enter="addTask"> </label>
        <button @click="addTask" type="submit">Add task</button>
        <br/>
    </div>
</template>

<script>
    export default {
        //props: ['task'],
        data() {
            return {
                task: ""
            }
        },
        methods: {
            addTask(event) {
                // string.trim() removes all whitespaces from
                // both sides of string.
                if (this.task.trim().length) {
                   /// console.log('NewEntry:', this.task)
                    this.$emit("newTask", this.task)
                    this.$refs.inputField.focus()
                    this.task = ""
                }
            }
        }
    }
</script>

<style scoped>

</style>