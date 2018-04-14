<template>
  <div id="app" class="jumbotron">
    <div class="container">
      <h1>Hello! Nice to meet you!</h1>
      <hr />
      <form @submit="addMessage">
        <div class="form-group">
          <input class="form-control" v-model="newMessage.title" type="text" maxlength="40" autofocus="true" placeholder="Please Introduce Yourself :)">
        </div>
        <div class="form-group">
          <textarea class="form-control" v-model="newMessage.text" placeholder="Leave your message!" rows="3"></textarea>
        </div>
        <button class="btn btn-primary btn-block" type="submit">Send</button>
      </form>
      <hr />
      <div class="card-group">
        <div class="card p-4" v-for="message in messages" v-bind:key="message.id">
          <div class="card-block">
            <h5 class="card-title">{{ message.title }}</h5>
            <p class="card-text">{{ message.text }}</p>
            <p class="card-text"><small class="text-muted">Added on {{ dateToString(message.timestamp) }}</small></p>
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
import { dateToString } from '../utils/utils'

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
  data () {
    return  {
      newMessage: {
        title: '',
        text: '',
        timestamp: null
      }
    }
  },
  methods: {
    addMessage (e) {
      e.preventDefault()
      if (this.newMessage.title === '') {
        return // nothing - kill function
      }
      this.newMessage.timestamp = Date.now()
      messagesRef.push(this.newMessage)
      this.newMessage.title = ''
      this.newMessage.text = ''
      this.newMessage.timestamp = null
    },
    dateToString: dateToString,
  },
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
