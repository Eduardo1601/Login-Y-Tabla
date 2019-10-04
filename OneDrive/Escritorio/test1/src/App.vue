<template>
  <div id="app">
  <img class="imagen" alt="Vue Esourse" src="./assets/Esourse.png" >
    <Login @click_login="status=1" v-if="status==0"></Login>
    <Table @agregado="status=4" @denegado="status=1" @tablas="status=4" @clinete="status=4" @aceptar="status=3" @logout="status=0" @nuevo="status=2" @Refrescar="status=1" @click_agregar="statu=0" v-else-if="status==1"></Table>
    <Registro @cancelar="status=1" @agregar="status=1" v-else-if="status==2"></Registro>
    <Clientes @regresar="status=1" @enviar="status=4" v-else-if="status==3"> </Clientes>
    <Table2 @regresar="status=1" v-else-if="status==4"></Table2>
  </div>
</template>

<script>
import Table from './components/Table.vue';
import Login from './components/Login.vue';
import HelloWorld from './components/HelloWorld.vue';
import Registro from './components/Registro.vue';
import Clientes from './components/Clientes.vue';
import Table2 from './components/Table2.vue';
export default {
  name: 'app',
  components: {
    // eslint-disable-next-line 
    HelloWorld,
    Table,
    Login,
    Registro,
    Clientes,
    Table2
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

.imagen{
width:60%;
height:40%;
 overflow: hidden;
 position:left;
  top: 0;

}
</style>
