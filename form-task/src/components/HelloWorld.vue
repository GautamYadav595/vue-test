<template>
  <div>
    <!-- Form Section -->
    <form @submit.prevent="submitForm">
      <label>First Name:</label>
      <input type="text" placeholder="Enter Your First Name" v-model="form.FirstName" required />
      <br />

      <label>Last Name:</label>
      <input type="text" placeholder="Enter Your Last Name" v-model="form.Lastname" required />
      <br />

      <label>Address:</label>
      <input type="text" placeholder="Enter Your Address" v-model="form.Address" required />
      <br />

      <button type="submit">Submit</button>
    </form>

    <hr />

    <!-- Table Section -->
    <table border="1">
      <thead>
        <tr>
          <th>First Name</th>
          <th>Last Name</th>
          <th>Address</th>
          <th>Edit Options</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="(entry, index) in formDataList" :key="index" :class="{ red: entry.isRed }">
          <td>{{ entry.FirstName }}</td>
          <td>{{ entry.Lastname }}</td>
          <td>{{ entry.Address }}</td>
          <td>
            <button @click="removeData(index)">X</button>
            <input type="checkbox" v-model="entry.isRed" />
            Red
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      form: {
        FirstName: "",
        Lastname: "",
        Address: "",
      },
      formDataList: [], // Array to store submitted data
    };
  },
  methods: {
    submitForm() {
      // Push the form data into the array with isRed defaulting to false
      this.formDataList.push({
        FirstName: this.form.FirstName,
        Lastname: this.form.Lastname,
        Address: this.form.Address,
        isRed: false, // Default state of checkbox
      });

      // Clear the form fields
      this.form.FirstName = "";
      this.form.Lastname = "";
      this.form.Address = "";
    },
    removeData(index) {
      this.formDataList.splice(index, 1); // Correctly removes the row at the given index
    },
  },
};
</script>

<style scoped>
table {
  width: 100%;
  border-collapse: collapse;
  margin-top: 20px;
}

th, td {
  padding: 8px;
  text-align: left;
  border: 1px solid black;
}

th {
  background-color: #f4f4f4;
}

.red {
  
  color: red;
}
</style>
