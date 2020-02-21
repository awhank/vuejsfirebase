<template>
  <div id="app" class="container">
    <div class="page-header">
      <h1>Vue js 2  FIrebase Sample Application</h1>
    </div>

    <div class="panel panel-default">
      <div class="panel-heading">
        <h3>Books Lists</h3>
      </div>
      <div class="panel-body">
        <table class="table table-striped">
          <thead>
            <tr>
              <th>
                Title
              </th>
              <th>
                Author
              </th>
            </tr>
          </thead>
          <tbody>
            <tr v-for="book in books">
              <td>
               <a v-bind:href="book.url">{{book.title}}</a> 
              </td>
              <td>
                {{book.author}}
              </td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
    <img src="./assets/logo.png">
    <router-view/>
  </div>
</template>

<script>
// import Firebase from 'firebase'
import firebase from 'firebase/app'
import 'firebase/database'

let config ={
  apiKey: "AIzaSyDveQyfTwxYgpg_hBXH9VtfjHOZ-Dv6uEo",
  authDomain: "vuejs-and-firebase-adb5c.firebaseapp.com",
  databaseURL: "https://vuejs-and-firebase-adb5c.firebaseio.com",
  projectId: "vuejs-and-firebase-adb5c",
  storageBucket: "vuejs-and-firebase-adb5c.appspot.com",
  messagingSenderId: "84882270501",
  appId: "1:84882270501:web:5833f22cdab2a6137852cc",
  measurementId: "G-B70TTHW4ND"
};

let app = Firebase.initializeApp(config);
let db = app.database();
console.log(db);

let booksRef = db.ref('books');

export default {
  name: 'App',
  firebase: {
    books: booksRef
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
