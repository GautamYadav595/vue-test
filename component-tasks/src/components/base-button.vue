<template>
    <button 
      v-on:click="handleClick" 
      :style="buttonStyle" 
      id="button"
    >
      Primary
    </button>
  </template>
  
  <script>
  export default {
    name: 'base-button',
    props: {
      changeStyle: Boolean, // Change prop type to Boolean
    },
    data() {
      return {
        msg: "This is an alert box",
        isStyled: false, // Controls button styling
      };
    },
    computed: {
      buttonStyle() {
        return this.isStyled
          ? { backgroundColor: 'red', color: 'black', padding: '20px', width: '110px' }
          : { backgroundColor: '#3023e4', color: 'white', padding: '20px', width: '110px' };
      }
    },
    methods: {
      handleClick() {
        if (this.changeStyle) {
          this.isStyled = !this.isStyled; // Toggle button style
        } else {
          alert(this.msg);
        }
      }
    }
  };
  </script>
  
  <style scoped>
  #button {
    font-size: 16px;
  }
  </style>
  