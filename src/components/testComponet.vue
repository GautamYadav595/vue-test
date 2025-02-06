<template>
    <div>
    <h1 id="hello"> {{hello}} {{ testing }}</h1>
    <input  v-model="hello"  >
    <button v-on:click="clear()">Click to clear input field</button>
    <br />
    <button v-on:click="makeCapital()">Click to convert in UpperCase</button>
</div>
</template>

<script>
export default{
    name: "testComponent",
    data: function () {
        return {
            hello : "",
            testing:"testing"
            }
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
