<template>
  <div v-if="gems">
    <button @click="changeItemTwo">Click to change number 2</button>
    <hr />ENTER HERE TO UPDATE YOUR ANSWERS:
    <form @submit.prevent="submitForm">
      <input type="radio" name="firstField" value="yes" v-model="formInfo.firstField"/>yes
            <input type="radio" name="firstField" value="no" v-model="formInfo.firstField"/>no
      <br/>
      <button type="submit">Submit</button>
      {{ formInfo.firstField }}
    </form>
  </div>
</template>

<script>
export default {
  name: "NestedComponent",
  props: {
    gems: Array,
    answers: Object
  },
  data: function() {
    return {
      formInfo: {}
    };
  },
  methods: {
    submitForm: function() {
        console.log('submitted!')
        console.log(this.formInfo)
        this.gems = this.formInfo;
        console.log(this.answers)
    },
    changeItemTwo: function() {
      console.log("Changing the second item now!");
      this.gems[1].name = "Number 2 change";
    }
  }
};
</script>

<style scoped>
</style>