<template>
<form>
  <p><label>Nom</label></p>
  <p><input name="Nom" ></p>
  <button :click="submit()"></button>
  </form>
</template>

<script>
import axios from 'axios'
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  methods:{
    submit(){
      axios.defaults.headers.post['Content-Type'] = 'application/x-www-form-urlencoded';
    axios.post('http://localhost/form/post.php','firstName=Fred&lastName=Flintstone')
  .then(function (response) {
    console.log(response);
  })
  .catch(function (error) {
    console.log(error);
  });
    }
  },
  mounted(){
    axios.get('https://api.chucknorris.io/jokes/random')
    .then(data => {
      console.log(data.data)
    })
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
