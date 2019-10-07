<html>
<body>
<p>
<img src="/assets/{{Esource.png}}" class="img-responsive" height="70" width="90">
</p>
</body>
</html>
<template>
<div>
       <div class="dis">
       <div class="login">
       <div class="tainer">
       <div class="cont">
       <div class="cuatro">
       <table>
       <div>
       </div>
         <button class="catorce" @click="nuevo()">Agregar Empleado</button>    
         <button class="quince" @click="tablas()"> Ver Tabla de Solicitudes </button>
    <button class="nueve" @click="aceptar()">Solicitud</button>
    <button class="diez" @click="logout()">Logout</button>
    
    </table>
    </div>
    <div>
    </div>
    <br>
    <br>
<table class="Hehe" border="1" align="center"  bordercolor="6F6F6F" cellspacing="0">
    <th class="volor" width="150" height="30" bgcolor="82E0AA">
        IdEmpleado
        </th>
        <th class="volor" width="150" height="30" bgcolor="82E0AA">
        Nombre
        </th>
        <th class="volor" width="150" height="30" bgcolor="82E0AA">
        Apellido
        </th>
        <th class="volor" width="150" height="30" bgcolor="82E0AA">
        Dpi
        </th>
        <th class="volor" width="150" height="30" bgcolor="82E0AA">
        Email
        </th>
         <th class="volor" width="150" height="30" bgcolor="82E0AA">
        Días
        </th> <th class="volor" width="150" height="30" bgcolor="82E0AA">
            Eliminar 
        </th>

        
    <tr v-for="todo in todos" :key="todo.id">
        
        <td bgcolor="82E0AA" > {{todo.id}}
        </td>
         <td bgcolor="#C5C3C3">{{todo.nombre}}
        </td>
        <td bgcolor="#C5C3C3">{{todo.apellido}}
        </td>
        <td bgcolor="#C5C3C3">{{todo.dpi}}
        </td>
        <td bgcolor="#C5C3C3">{{todo.email}}
        </td>
        <td bgcolor="#C5C3C3">{{todo.diasDisponibles}}
        </td>

        <div class="tres">
        <td>
        <button class="btn" @click="deleteEmpleado(todo.id)">Borrar</button>
        </td>
        </div>
            </tr>
     </table>
     </div>
     </div>
     </div>
    </div>
    </div>
</template>
<script>
import axios from 'axios'
export default {
    name: 'Table',
    data(){
        return{
            todos:null,
        }
    }, 
    mounted (){
        this.getTodos();
    },
    methods:{
        nuevo(){
            this.$emit("nuevo");
        },
        logout(){
           this.$emit("logout");
          /*$IdEmpleado = $_POST['IdEmpleado'];
          $Nombre = $_POST['Nombre'];
          $Apellido = $_POST['Apellido'];
          $DPI = $_POST['DPI'];
          $Email= $_POST['Email'];
            */
        },
        aceptar(){
           this.$emit("aceptar");
        },
        agregado(){
           this.$emit("agregado");
        },
        denegado(){
           this.$emit("denegado");
        },
        tablas(){
           this.$emit("tablas");
        },
        getTodos(){
            axios 
            .get('http://localhost:3000/empleados',{
            })
            .then(response => {
                // eslint-disable-next-line 
                console.log(response)
                this.todos=response.data

            })
            // eslint-disable-next-line 
            .catch(e=> console.log(e))
        },
        Refrescar(){
           this.getTodos();
        },
        deleteEmpleado(idEmpleado){
             axios.delete('http://localhost:3000/eliminarEmpleado/'+ idEmpleado)
            .then(response => {
                this.getTodos();
                // eslint-disable-next-line
                console.log(response.data)
            }).catch(e => {
                // eslint-disable-next-line
                console.log(e)
            })
        }
    }
}
</script>




<style>

html,body { 
  background:white;  padding: 0px; margin: 0px; width: 100%;  height: 100vh;  font-family: "Roboto";   color:#333; }

.cuatro {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: ;

}

li {
  float: left;
}

li a {
  display: block;
  color: black;
  text-align: center;
  padding: 14px 20px;
  text-decoration: none;
}

li a:hover {
  background-color: black;
}

.active {
  background-color: #0F7EE1;
}

.GRIPE {
  background-color: #0F7EE1;
}

.TOS {
  background-color: #0F7EE1;
}


.catorce
{
background: #82E0AA ;
}

.quince{
    background: #82E0AA ;
}

.nueve{
    background: #82E0AA ;
}

.diez{
    background: #82E0AA ;
}

.dos {
width: 30%;
    max-width: 300px;
    background:  ;
    padding: 20px;
    border-radius: 10px;
    
    
},
 .btn {
    background: blue;
}

button, th,  {
    align:center;
    right: 20px;
border-radius: 10px;
align:center;
}

.dis{

 width: 200%;
    max-width: 1300px;
    background:#;
    padding: 10px;
    border-radius: 5px;
    display: inline-block;
    align-items: center;
},

.login .tainer .cont{
    width: 6%;
    max-width: 5px;
    text-align: center center; 

}


.login .tainer .cont input.error, {    
    padding: 5px 6px;
    background-color: white;
    color: #;
    text-align: center;
}
table {
  font-family: Verdana;
  border-collapse: collapse;
  width: 80%;

}

td, th, table{
  border: 0px solid #dddddd;
  text-align: left;
  padding: 12px;
    border-radius: 5px;
  text-align: center;
  font-family: Tahoma;
  font-size: 27px;
}

tr:nth-child(even),{
  background-color:;
}
.cuatro {
  list-style-type: none;
  margin:;
  padding:;
  overflow: hidden;
  background-color:rgb(60.60.60);
}

.cuatro {
  float: ;
}


button a:hover {
  background-color: white;
}

body {margin:0;}

  .cuatro {
  list-style-type: none;
  margin: ;
  padding: ;
  overflow: hidden;
  background-color: ;
  position:fixed;
  top: 0;
}

 .trece {
 background-color:#0F7EE1;
}

button {
  float: left;
}

.cuatro button{
  display: block;
  color: black;
  text-align: center;
  padding: ;
  text-decoration: none;
}

button a:hover:not(.active) {
  background-color: black;
}

.cuatro {
  background-color: ; 
}
</style>