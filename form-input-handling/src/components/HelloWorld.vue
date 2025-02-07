<template>
  <div class="hello">
    <h1>Form Input Handling</h1>

    <input v-model="message" placeholder="Enter a text">
    <p> entered text is : {{ message }}</p>
    <br />

    <span>Multiline Message is </span>
    <p>{{ message2 }}</p>
    <br />
    <textarea v-model="message2" placeholder="Enter a multiline text"></textarea>
    <br />

    <span>checkbox</span>
    <br />
    <input type="checkbox" id="checkbox" v-model="checked">
    <label>{{ checked }}</label>
    <br />
    <br />
    <span>Java</span>
    <input type="checkbox" id="checkbox" value="java" v-model="skills">
    <br />
    <span>Python</span>
    <input type="checkbox" id="checkbox" value="Python" v-model="skills">
    <br />
    <span>JavaScript</span>
    <input type="checkbox" id="checkbox" value="Javascript" v-model="skills">
    <br />
    <br />

    <span> checked properties are {{ skills }}</span>
    <br />
    <br />
    <div>
      <span>Radio Buttons</span> <br />
      <label>ReactJs</label>
      <input type="radio" id="radio" value="ReactJs" v-model="FrontendTech">
      <br />
      <label>NextJs</label>
      <input type="radio" id="radio" value="Nextjs" v-model="FrontendTech">
      <br />
      <label>Vuejs</label>
      <input type="radio" id="radio" value="VueJs" v-model="FrontendTech">
      <br />
      <span>Your Frontend Technology is {{ FrontendTech }}</span>
  </div>
  <div>
    <select v-model="gender">
    <span>Single Select from Multiple options</span>
    <option disabled value="">What is your Gender</option>
    <option >Male</option>
    <option >Female</option>
    <option >Other</option>
  </select>
  <br />
  <span>Selected Gender is {{ gender }}</span>
  </div>
  <div>
    <select v-model="selected">
      <option v-for="option in options" v-bind:value="option.value"  :key="option.text">{{ option.text }}</option>
    </select>
    <br />
    <span>Selected Option is {{ selected }}</span>
</div>
<br />

<div> Lazy input
  <input v-model.lazy="msg"> 
  <br />
  <span>Lazy input will show here : {{ msg }}</span>
  </div>

  <div> (.Number ) Example :Enter your age
  <input v-model.number="age">
  <br />
  <span>Your age is : {{ age }}</span>
  </div>
  <br />
  <div>.trim Example : Enter a string with trailing spaces
    <input v-model.trim="trimstr">
  </div>
  <span>Trimmed String is : {{ trimstr }}</span>

</div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data(){
    return {
      message: '',
      message2: '',
      msg:'',
      age:'',
      trimstr:'',
      checked: false,
      skills: [],
      FrontendTech:'',
      gender:'',
      selected: 'A',
      options: [
        { text: 'one', value: 'A' },
        { text: 'two', value: 'B' },
        { text: 'three', value: 'C' }
      ]
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
