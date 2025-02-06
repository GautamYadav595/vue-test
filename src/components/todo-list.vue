<template>
    <div id="todo-list-example">
        <form v-on:submit.prevent="addNewTodo">
            <label for="new-todo">Add a new Todo</label>
            <br />
            <input
            v-model="newTodoText"
            id="new-todo"
            placeholder="Enter new Todo Task"
            >
            <button>Add</button>
        </form>
        <ul>
            <TodoItem   
                v-for="(todo, index) in todos"
                :key="todo.id"
                :todo="todo"
                v-on:remove="removeTodo(index)"
                v-on:edit="editTodo(index, $event)"
                ></TodoItem>
           </ul>
    </div>
</template>

<script>
import TodoItem from "./TodoItem.vue"
export default{
    name: "TodoList",
    components: { TodoItem },
    data() {
        return {
     newTodoText: "",
     todos :
[
    { id: 1, title: "Take a Shower" },
    { id: 2, title: "prepare to cook Food" },
    { id: 3, title: "Coock food" },
    { id: 4, title: "Eat food"},
    { id: 5, title: "Sleep"}
],
nextTodoId :  6, 
        }
 },
 methods:{
    addNewTodo : function(){
        if(this.newTodoText.trim() !== ""){
        this.todos.push({
            id:this.nextTodoId++,
            title: this.newTodoText,
            isEditing: false,
        });
        this.newTodoText = "";
    }
    },
 
    removeTodo : function(index){
    this.todos.splice(index,1);
 },
 editTodo : function(index, newTitle){

   this.todos[index].title = newTitle;
   this.todos[index].isEditing = false;
 }
}
}

</script>
