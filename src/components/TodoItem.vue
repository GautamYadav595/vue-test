<template>
    <li>
        <span v-if="!isEditing">{{ todo.title }}</span>
        <input v-else v-model="editedText" @keyup.enter="saveEdit">
        <button @click="toggleEdit">{{ isEditing ? 'Save' : 'Edit' }}</button>
        <button @click="removeTodo">Remove</button>
    </li>
</template>

<script>
export default{
    props: ['todo'],
    
    data(){
        return{
            isEditing: false,
            editedText: this.todo.title
            }
        },
        methods:{
            toggleEdit(){
                if(this.isEditing)
            {
                this.saveEdit();

            }
            else{
                this.isEditing = true;
            }
            },
            saveEdit(){
                if(this.editedText.trim() !== "")
            {
                this.$emit("edit", this.editedText);
            }
            this.isEditing = false;
        },
        removeTodo()
        {
            this.$emit("remove");
        }
}
}
</script>