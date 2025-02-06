<template>
    <div>
    <h1 id="hello"> {{hello}} {{ testing }}</h1>
    <br />
    <br />
    {{ date }}
    <br />
    <input  v-model="hello"  >
    <button v-on:click="clear()">Click to clear input field</button>
    <button v-on:click="makeCapital()">Click to convert in UpperCase</button>
</div>
</template>

<script>
export default{
    name: "testComponent",
    data: function () {
        return {
            hello : "",
            testing:"testing",
            date: false
            }
    },
    created : function(){
        console.log("Created is Running")
        this.date = new Date();
    },
    mounted : function(){
        console.log("Mounted is Running")
        this.date = new Date();
    },
    updated : function(){
        console.log("Updated is Running")
    },
    detsroyed : function(){
        console.log("Destroyed is Running")
        this.date = new Date();
    },
    methods: {
        clear: function(){
            this.hello = ""
        },
         makeCapital: function(){
            this.hello = this.hello.toUpperCase();
         }
    }
}
</script>

<style scoped>

</style>
