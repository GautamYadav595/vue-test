<template>
  <div id="testing">
    <p>{{ name }} Testing</p>
    <div v-bind:style="{ color: color_value.color }">{{ name }} Testing</div>
    <h1 id="hello">{{ hello }} {{ testing }}</h1>
    <br />
    <br />
    {{ date }}
    <br />
    <input v-model="hello" />
    <button v-on:click="clear">Click to clear input field</button>
    <button v-on:click="makeCapital">Click to convert in UpperCase</button>
    <p>Has published Books {{ publishedBooksMessage }}</p>
    <input
      :checked="isRed"
      v-model="isRed"
      type="radio"
      v-on:click="red"
      for="color"
    />Red
    <input
      :checked="isyellow"
      v-model="isyellow"
      type="radio"
      v-on:click="yellow"
      for="color"
    />Yellow
    <input
      :checked="isGreen"
      v-model="isGreen"
      type="radio"
      v-on:click="green"
      for="color"
    />Green

    <br />
    <input type="text" v-model="name" />

    <select v-model="color_value">
      <!-- <option v-bind:value="{color: 'red'}">red</option>
            <option v-bind:value="{color: 'yellow'}">yellow</option>
            <option v-bind:value="{color: 'black'}">black</option>
            <option v-bind:value="{color: 'orange'}">orange</option> -->
      <option
        v-for="(col, index) in colors"
        v-bind:key="index"
        v-bind:value="{ color: col }"
      >
        {{ col }}
      </option>
    </select>
    <ul id="lsit">
      <li v-for="(item, index) in items" :key="item">
        {{ index }}  - {{ item }} 
      </li>
    </ul>
    <ul id="lsit">
      <li v-for="(item,name, index) in object" :key="item">
        {{ index }} - {{ name }} - {{ item }} 
      </li>
    </ul>
    <br />
    <span v-for="items in numbers" :key="items">
        {{ items }},
    </span>
    
    <button @click="evenNumbers">even Numbers</button>
    <div v-if="show">
    <span  v-for="number in evenNumbersList" :key="number">{{ number }},</span>
</div>
<button @click="oddNumbers">odd Numbers</button>
    <div v-if="shows">
    <span  v-for="number in oddNumbersList" :key="number">{{ number }},</span>
</div>
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
      isRed: false,
      isyellow: false,
      isGreen: false,
       show: false,
       shows: false,
       evenNumbersList: [],
       oddNumbersList: [],
      items: ["Java", "jabvaScript", "HTML", "CSS", "ReactJs", "TailwindCSS"],
      colors: ["red", "yellow", "black", "orange"],
      numbers: [1,2,3,4,5,6,7,8,9,10,11,12],
      color_value: {
        color: "black",
      },
      author: {
        name: "John Doe",
        books: [
          "Vue 2 - Let's Grid",
          "Vue 3 - Let's Grid",
          "Vue 4 - Let's Grid",
        ],
      },
      object:{
        name: "Gautam Yadav",
        age: "22",
        email: "test@gmail.com"
      }
    };
  },
  computed: {
    publishedBooksMessage() {
      return this.author.books.length > 0 ? "Yes" : "No";
    },
    
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
    },
    red: function () {
      // eslint-disable-next-line
      console.log(this.isRed);
      this.isRed = this.redbox === "yes";
    },
    yellow: function () {
      this.isyellow = this.yellowbox === "yes";
    },
    green: function () {
      this.isGreen = this.greenbox === "yes";
    },
    evenNumbers() {
    this.evenNumbersList = this.numbers.filter(number => number%2 === 0);
    this.show = true;
    },
    oddNumbers() {
    this.oddNumbersList = this.numbers.filter(number => number%2 != 0);
    this.shows = true;
}

  },
};
</script>

<style >
.red {
  color: red;
}
.green {
  color: green;
}
.yellow {
  color: yellow;
}
</style>
