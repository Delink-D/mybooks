<template>
  <div class="home">
    <span v-for="book in localFirebase.books">
      book - {{book.name}}
    </span>
  </div>
</template>

<script>
  import environment from '../../config/env'
  import firebase from 'firebase'

  /** Initialize Firebase */
  let config = {
    apiKey: environment.firebase.apiKey,
    authDomain: environment.firebase.authDomain,
    databaseURL: environment.firebase.databaseURL,
    projectId: environment.firebase.projectId,
    storageBucket: environment.firebase.storageBucket,
    messagingSenderId:environment.firebase.messagingSenderId 
  };

  let app = firebase.initializeApp(config);
  let db = app.database();
  let booksRef = db.ref('books');

  export default {
    name: 'HomeComponent',
    data () {
      return {
        localFirebase: {
          books: booksRef
        }
      }
    }
  }
</script> 

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>

</style>
