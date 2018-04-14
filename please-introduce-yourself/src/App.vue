<template>
  <div id="app" class="jumbotron">
    <div class="container">
      <h1>Hello! Nice to meet you!</h1>
      <hr>
      <div class="card-group">
        <div class="card" v-for="message in messages" v-bind:key="message.id">
          <div class="card-block">
            <h5 class="card-title">{{ message.title }}</h5>
            <p class="card-text">{{ message.text }}</p>
            <p class="card-text"><small class="text-muted">Added on {{ message.timestamp }}</small></p>
          </div>
        </div>
      </div>
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
