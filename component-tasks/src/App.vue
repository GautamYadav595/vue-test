<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    
    <!-- Multiple Button Counter Components -->
    <buttonCounter aler />
    <buttonCounter />
    <buttonCounter changeStyle/>

    <!-- Rendering BlogPost Components Dynamically -->
    <blog-post
      v-for="post in posts"
      :key="post.id"
      :title="post.title"
      :content="post.content"  
    ></blog-post>
    <baseButton /> <!-- This will trigger the alert -->
    <baseButton :changeStyle="true" />
    <br />
    <testCompo />
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue';
import buttonCounter from './components/button-counter.vue';
import BlogPost from './components/blog-post.vue'; // Ensure correct naming
import baseButton from './components/base-button.vue';
import testCompo from './components/testCompo.vue';
export default {
  name: 'App',
  components: {
    HelloWorld,
    buttonCounter,
    BlogPost, // Fixed component name
    baseButton,
    testCompo
  },
  data() {
    return {
      posts: [
        { id: 1, title: 'My Journey with Vue', content: '<p>This is my Vue journey.</p>' },
        { id: 2, title: 'Why I love Vue', content: '<p>Vue is reactive and easy to use.</p>' },
        { id: 3, title: 'My Favorite Vue Features', content: '<p>Vue directives are powerful.</p>' }
      ]
    };
  },
  changeStyle: function(){
    console.log('changeStyle called');
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
