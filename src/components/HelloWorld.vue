<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div v-for="user in users" class="Author">
         <h2>{{user.Title}}</h2> 
         <img :src="user.Image">
         <h3>Author: {{user.Author}}</h3>
    </div>
    
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome to My Api',
      users: []
    }
  },
  created: function(){
    fetch('http://localhost:8000/data')
    .then(r => r.json())
    .then(json => {
        this.users = json;
    });
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 10px 10px;

}
img {
  object-fit: cover;
  height: 300px;
  width: 25%;
}
li Title {
  color: #42b983;
}
h1 {
  text-align: center;
  color: grey;

}
h2 {
  text-align: center;
  color: lightblue;

}
</style>
