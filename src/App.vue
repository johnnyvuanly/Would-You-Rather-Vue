<template>
  <div id="app">
    
    <h1>Would you rather...</h1>

    <would-you-rather
      v-for="questions in question"
      v-bind:key="questions.id" 
      v-bind:question="questions.wyrQuestion"
      v-bind:answer1="questions.wyrAnswer1"
      v-bind:answer2="questions.wyrAnswer2"
      v-on:answer-changed="answerChanged">
    </would-you-rather>

    <ul>
      <li v-for="userMessage in userSelectionMessage">{{ userMessage.userChoice}}</li>
    </ul>

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
      question: [
        {
          id: 0,
          wyrQuestion: 'Would you rather lose the ability to lie or believe everything you’re told?',
          wyrAnswer1: 'Lose ability to lie',
          wyrAnswer2: 'Believe everything you\'re told'
        },
        {
          id: 1,
          wyrQuestion: 'Would you rather be in jail for a year or lose a year off your life?',
          wyrAnswer1: 'Jail for a year',
          wyrAnswer2: 'Lose a year of your life'
        },
        {
          id: 2,
          wyrQuestion: 'Would you rather go back to age 5 with everything you know now or know now everything your future self will learn?',
          wyrAnswer1: 'Go back to age 5 with everything you know now',
          wyrAnswer2: 'Know now everything your future self will learn'
        },  
      ],
      userSelectionMessage: [] // Empty because user hasn't chose anthing yet
    }
  },
  methods: {
    answerChanged(choice) { // arguement to this method "choice" is being sent from this.choice from WouldYouRather
      let userAnswer = {userChoice: `You chose "${choice}."`}
      this.userSelectionMessage.push(userAnswer)
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

