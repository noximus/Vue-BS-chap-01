<template>
  <div id="app">
    <div v-for="message in messages">
      <h4>{{ message.title }}</h4>
      <p>{{ message.text }}</p>
      <p>{{ message.timestamp }}</p>
    </div>
    <!-- <router-view/> -->
  </div>
</template>

<script src="https://www.gstatic.com/firebasejs/4.12.1/firebase.js"></script>
<script>
  // Initialize Firebase

</script>
<script>
import Firebase from 'firebase'

let config = {
  apiKey: "AIzaSyCvg-CVhjGw0nwkcO1BO7a0VhZkOIILRbw",
  authDomain: "pleaseintroduceyourself-70e90.firebaseapp.com",
  databaseURL: "https://pleaseintroduceyourself-70e90.firebaseio.com",
  projectId: "pleaseintroduceyourself-70e90",
  storageBucket: "pleaseintroduceyourself-70e90.appspot.com",
  messagingSenderId: "736569888183"
};
let app = Firebase.initializeApp(config)
let db = app.database()
let messagesRef = db.ref('messages')
export default {
  name: 'app',
  firebase: {
    messages: messagesRef
  }
}

</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
