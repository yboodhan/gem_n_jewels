<template>
  <div class="hello">
    <h1>{{ msg }}</h1>

  <div v-if="gems">
    <div v-for="gem in gems" v-bind:key="gem.id">
      {{ gem.id }}: {{ gem.name }}
      {{ gem.description }}
      ${{ gem.price }}
      In stock? {{ gem.in_stock ? "Yes": "No"}}
    <hr/>
    </div>
    <button @click="changeItem"> Click to change item 1 </button>
    <NestedComponent v-bind:gems.sync="gems" v-bind:answers.sync="answers"/>
  </div>
  </div>
</template>

<script>
import NestedComponent from './NestedComponent.vue'

export default {
  name: "HelloWorld",
  props: {
    msg: String,
    gems: Array,
    answers: Object
  },
  components: {
    NestedComponent
  },
  methods: {
    changeItem: function() {
      console.log('Changing the first item now!');
      this.gems[0].name = "Changed name here";
    }
  }
};
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
