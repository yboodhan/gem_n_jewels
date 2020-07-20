<template>
  <div id="app">
    <p v-if="gems">{{ gems[0].name }} </p>
    <p v-if="gems">{{ gems[1].name }} </p>
    <p v-if="gems">{{ gems[2].name }} </p>
    <button v-if="gems" @click="changeItemThree"> Click to change number three</button>
    <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App" v-bind:gems.sync="gems"/>
  </div>
</template>

<script>
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'App',
  components: {
    HelloWorld
  },
  data: function() {
    return {
      gems: null
    };
  },
  methods: {
    changeItemThree: function() {
      console.log('Changing the third item now!');
      this.gems[2].name = "Number 3 changed to this";
    }
  },
  async beforeMount() {
      try {
        let jsonData = await require("./assets/jewel_data.json");
        if (!jsonData) {
          console.log("No data could be found.");
          this.gems = [];
        } else {
          console.log("The following data was found.");
          console.log(jsonData);
          this.gems = jsonData;
        }
      } catch (err) {
        console.log("We got an error", err);
        this.gems = [];
      }
  }
}
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
