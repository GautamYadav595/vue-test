<template>
    <div>
      <div>
        <input placeholder="Enter your text" v-model="text" />
        <button v-on:click="handleSubmit">Submit</button>
      </div>
      
      <table border="1">
        <thead>
          <tr>
            <th>Entered Text</th>
            <th>Options</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="(entry, index) in listofinput" :key="index">
            <td>
              <span v-if="editingIndex !== index">{{ entry }}</span>
              <input v-else v-model="editedText" />
            </td>
            <td>
              <button @click="removeData(index)">X</button>
              <button v-if="editingIndex !== index" @click="startEditing(index, entry)">Edit</button>
              <button v-else @click="saveEdit(index)">Save</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </template>
  
  <script>
  export default {
    name: 'testCompo',
    data() {
      return {
        text: "",
        listofinput: [],
        editingIndex: null, // Track which row is being edited
        editedText: "" // Store the new text input
      };
    },
    methods: {
      handleSubmit() {
        if (this.text.trim() !== "") {
          this.listofinput.push(this.text);
          this.text = "";
        }
      },
      removeData(index) {
        this.listofinput.splice(index, 1);
      },
      startEditing(index, entry) {
        this.editingIndex = index;
        this.editedText = entry;
      },
      saveEdit(index) {
        if (this.editedText.trim() !== "") {
          this.listofinput[index] = this.editedText;
        }
        this.editingIndex = null; // Exit edit mode
      }
    }
  };
  </script>
  