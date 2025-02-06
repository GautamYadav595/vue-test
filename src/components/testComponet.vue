<template>
    <div>
        <h1 id="hello"> {{ hello }} {{ testing }}</h1>
        <br />
        <br />
        {{ date }}
        <br />
        <input v-model="hello">
        <button v-on:click="clear">Click to clear input field</button>
        <button v-on:click="makeCapital">Click to convert in UpperCase</button>
        <p> Has published Books {{ publishedBooksMessage }}</p> 
    </div>
</template>

<script>
export default {
    name: "testComponent",
    data() {
        return {
            hello: "",
            testing: "testing",
            date: false,
            author: {
                name: 'John Doe',
                books: [
                    'Vue 2 - Let\'s Grid',
                    'Vue 3 - Let\'s Grid',
                    'Vue 4 - Let\'s Grid',
                ]
            }
        };
    },
    computed: {
        publishedBooksMessage() {
            return this.author.books.length > 0 ? 'Yes' : 'No';
        }
    },
    created() {
        console.log("Created is Running");
        this.date = new Date();
    },
    mounted() {
        console.log("Mounted is Running");
        this.date = new Date();
    },
    updated() {
        console.log("Updated is Running");
    },
    
    methods: {
        clear() {
            this.hello = "";
        },
        makeCapital() {
            this.hello = this.hello.toUpperCase();
        }
    }
};
</script>

<style scoped>
</style>
