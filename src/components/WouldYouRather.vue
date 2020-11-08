<template>
  <div class="wyr">
    
    <h2>Please make your choice!</h2>

    <h3>{{ question }}</h3>

    <!-- v-bind sets radio buttons value -->
    <input type="radio" v-model="choice" v-bind:value="answer1" v-on:change="choiceMade"> 
    <label>{{ answer1 }}</label>
    <input type="radio" v-model="choice" v-bind:value="answer2" v-on:change="choiceMade">
    <label>{{ answer2 }}</label>

  </div>
</template>

<script>
export default {
  name: 'WouldYouRather', // App.vue is the parent
  props: { // props and data treated similarly, prop provided by parent
    question: String,
    answer1: String,
    answer2: String
    // Never modify prop in a component
  },
  data() { // data is a function that returns an object of the above components data
    return {
      choice: '' // Empty string to represent no choice was made
    }
  },
  methods: {
    choiceMade() {
      // emit a message named 'answer-change' this is an event
      // dashes for event names are good because it won't conflict with a JavaScript name
      // this.choice is listing data that we want sent as a part of the message to the parent 
      this.$emit('answer-changed', this.choice)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
.wyr {
  border: 2px black solid;
  background: lightcyan;
  margin: 10px;
}
</style>
