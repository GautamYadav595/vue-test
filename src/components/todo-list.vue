<template>
    <div id="todo-list-example">
        <form v-on:submit.prevent="addNewTodo">
            <label for="new-todo">Add a Todo</label>
            <input
            v-model="newTodoText"
            id="new-todo"
            placeholder="Enter new Todo Task"
            >
            <button>Add</button>
        </form>
        <ul>
            <li is ="todo-item" 
                v-for="(todo, index) in todos"
                v-bind:key="todo.id"
                v-bind:title="todo.title"
                v-on:remove="todos.splice(index,1)"
                >

            </li>

        </ul>

    </div>
</template>

<script>
export default{
    name: "#todo-list",
    data() {
        return {
     newTodoText: "",
     todos :
[
    {
        id:1,
        title: 'Take a Shower'
    },
    {
        id: 2,
        title: "prepare to cook Food"
    },
    {
        id: 3,
        title: "Coock food"
    },
    {
        id: 4,
        title: "Eat food"
    },
    {
        id: 5,
        title: "Sleep"
    }
] ,
nextTodoId :  6, 
        }
 },
 methods:{
    addNewTodo : function(){
        this.toodos.push({
            id:this.nextTodoId++,
            title: this.newTodoText
        })
        this.newTodoText = ""
    }
 }

}
</script>
