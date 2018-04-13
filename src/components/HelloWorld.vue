<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <ul>
      <li><a v-on:click="sayHello">hello</a></li>
      <li><a v-on:click="getHello">get hello from api</a></li>
    </ul>
  </div>
</template>

<script>
import $ from '@/../static/js/jquery'

export default {
  name: 'HelloWorld',
  data: function () {
    return {
      msg: 'Welcome to Your Vue.js App'
    }
  },
  methods: {

    sayHello: function sayHello () {
      this.msg = 'hello there '
    },

    getHello: function getHello () {
      var vue = this;
      return $.ajax({
        type: 'GET',
        url: '/api/v1/index/hello',
        dataType: 'json',
        success: function (data) {
          console.log(data)
          vue.msg = data
        }
      });
    }

  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
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
