<template>
    <div v-if="gems">
        <button @click="changeItemTwo"> Click to change number 2 </button>
    </div>
</template>

<script>
export default {
name: "NestedComponent",
  props: {
    gems: Array
  },
  methods: {
    changeItemTwo: function() {
      console.log('Changing the second item now!');
      this.gems[1].name = "Number 2 change";
    }
  }
};
</script>

<style scoped>

</style>