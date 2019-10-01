<template>
  <div id="app">
    <Login @click_login="status=1" v-if="status==0"></Login>
    <Table @logout="status=0" @nuevo="status=2" @click_agregar="statu=0" v-if="status==1"></Table>
    <Registro @cancelar="status=1" @agregar="status=1" v-if="status==2"></Registro>
    
  </div>
</template>

<script>
import Table from './components/Table.vue';
import Login from './components/Login.vue';
import HelloWorld from './components/HelloWorld.vue';
import Registro from './components/Registro.vue';

export default {
  name: 'app',
  components: {
    // eslint-disable-next-line 
    HelloWorld,
    Table,
    Login,
    Registro
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
