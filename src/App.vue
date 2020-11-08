<template>
  <div id="app">
    
    <h1>Would you rather...</h1>

    <would-you-rather 
    v-bind:question="wyrQuestion"
    v-bind:answer1="wyrAnswer1"
    v-bind:answer2="wyrAnswer2"
    v-on:answer-changed="answerChanged"></would-you-rather>

    <p>{{ userSelectionMessage }}</p>

    <!-- would-you-rather is listening for answer-changed event, answerChanged is method created below-->
    <!-- <WouldYouRather></WouldYouRather> will work too. Above is the name of the file-->

  </div>
</template>

<script>
// App.vue is sending data to WouldYouRather via props v-bind data. WouldYouRather is comminucating to its parent by emitting an event
import WouldYouRather from './components/WouldYouRather.vue'

export default {
  name: 'App',
  components: {
    WouldYouRather
  },
  data() {
    return{
      wyrQuestion: 'Would you rather lose the ability to lie or believe everything you’re told?',
      wyrAnswer1: 'Lose ability to lie',
      wyrAnswer2: 'Believe everything you\'re told',
      userSelectionMessage: '' // Empty because user hasn't chose anthing yet
    }
  },
  methods: {
    answerChanged(choice) { // arguement to this method "choice" is being sent from this.choice from WouldYouRather
      this.userSelectionMessage = `Thanks you chose ${choice}`
    }
  }
}
</script>

<style>
body {
  background: lightskyblue;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
  background: lightgreen;
}
</style>

