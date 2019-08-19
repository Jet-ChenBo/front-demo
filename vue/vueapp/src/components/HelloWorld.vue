<template>
  <div class="hello">
      <h3>我是axios APP，用来发送请求，拦截响应</h3>
      <button @click="getData">发送请求</button>
      <ul>
        <li v-for="item in items">
          {{item.title}}
        </li>
      </ul>
  </div>
</template>

<script>
  import Vue from 'vue'
  Vue.prototype.$http = axios;
  import axios from 'axios'

export default {
  name: 'HelloWorld',
  data () {
    return {
        items:[]
    }
  },
  methods:{
    getData(){
      var self = this
      this.$http.get('https://cnodejs.org/api/v1/topics',{
        params:{
          page:1,
          limit:10
        }
      })
      .then(function(res){
        self.items = res.data.data
        console.log(res)
      })
      .catch(function(err){
        console.log(err)
      })
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
