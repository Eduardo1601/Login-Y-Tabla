<template>
  <div id="app">
    <Login @click_login="status=1" v-if="status==0"></Login>
    <Table @logout="status=0" v-else-if="status==1"></Table>

  </div>
</template>

<script>
import Table from './components/Table.vue'
import Login from './components/Login.vue'
import HelloWorld from './components/HelloWorld.vue'

export default {
  name: 'app',
  components: {
    // eslint-disable-next-line 
    HelloWorld,
    Table,
    Login
  },
  data(){
    return {
      status: 0
    }
},
 methods:{
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
