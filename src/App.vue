<template>
  <div id="app">
      {{quote}}
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'app',
    data () {
      return {
        quote: ''
      };
    },
    created: function() {
      this.quote ='Loading...';
      this.loadQuotes();
    },
    methods: {
      loadQuotes: function(){
          var vm = this;
          axios.get('http://ron-swanson-quotes.herokuapp.com/v2/quotes')
          .then(function(response) {
             vm.quote=response.data[0]; 
          }).catch(function(error){
             vm.quote='An error occured: ' + error;
          });
      }
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
