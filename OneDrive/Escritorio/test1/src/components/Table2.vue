<template>
    <div>
    <div class="dis">
    <div class="login">
       <div class="tainer">
       <div class="veinte">
     <table>
          <th>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
          <li><a></a></li>
              <li><a></a></li>
          <button @click="Refrescar()">Refrescar</button>
          <button @click="regresar()">Regresar</button>
       </th>
       </table>
       </div>
    </div>
    </div>
<table border="1" align="center"  bordercolor="6F6F6F" cellspacing="0">
    <th class="volor" width="150" height="30" bgcolor="82E0AA">
        idSolicitud
        </th>
        <th class="volor" width="150" height="35" bgcolor="82E0AA">
        Nombre
        </th>
         <th class="volor" width="150" height="35" bgcolor="82E0AA">
        Apellido
        </th >
         <th class="volor" width="220" height="35" bgcolor="82E0AA">
        Fecha
        </th>
         <th class="volor" width="150" height="35" bgcolor="82E0AA">
        Días Solicitados
        </th>
        <th class="volor" width="150" height="35" bgcolor="82E0AA">
         Status
        </th>

        
    <tr v-for="todo in todos" :key="todo.idSolicitud">
        
        <td bgcolor="82E0AA" > {{todo.idSolicitud}}
        </td>
         <td bgcolor="white">{{todo.nombre}}
        </td>
        <td bgcolor="white">{{todo.apellido}}
        </td>
        <td bgcolor="white">{{date(todo.fecha)}}
        </td>
        <td bgcolor="white">{{todo.diasSolicitados}}
        </td>
        <td bgcolor="white">{{todo.status}}
        </td>
        <td>
        <button class="btn" @click="deleteSolicitud(todo.idSolicitud)">Borrar</button>
        </td>
 </tr>
     </table>
</div>
     </div>
     </template>
     <script>
import axios from 'axios'
import moment from 'moment'
export default {
    name: 'Table2',
    data(){
        return{
            todos:null,
            status:0
        }
    },
    mounted (){
        this.getTodos();
    },
 methods: {
    getTodos(){
            axios 
            .get('http://localhost:3000/solicitudes',{
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
        regresar(){
            this.$emit("regresar");
        },
        deleteSolicitud(idSolicitud){
             axios.delete('http://localhost:3000/eliminarSolicitud/'+ idSolicitud)
            .then(response => {
                this.getTodos();
                // eslint-disable-next-line
                console.log(response.data)
            }).catch(e => {
                // eslint-disable-next-line
                console.log(e)
            })
        },
        date(value){
         if (value) {
           return moment(String(value)).format('YYYY-MM-DD')
          }
        },
        agregado(){
            this.status=1        
        }        
    }
 }
</script>

<style>
button, th, td {
    align:center;
    right: 20px;
border-radius: 0px;
align:center;
}

.cuatro {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: black;
}

td, th, table{
  border: 0px solid #dddddd;
  text-align: left;
  padding: 12px;
  text-align: center;
}

tr:nth-child(even), .tres{
  background-color:;
}
.cuatro {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: #;
}

.cuatro {
  float: center;
}


button a:hover {
  background-color: black;
}

body {margin:0;}

  .cuatro {
  list-style-type: none;
  margin:;
  padding:;
  overflow: hidden;
  background-color: ;
  position:fixed;
  top: 0;
  width: 75%;
}

button {
  float: left;
}

.cuatro button{
  display: block;
  color: black;
  text-align: center;
  padding: 14px 16px;
  text-decoration: none;
}

button a:hover:not(.active) {
  background-color: #111;
}

.cuatro {
  background-color: ; 
}

table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 80%;
}

td, th, table{
  border: 0px solid #dddddd;
  text-align: left;
  padding: 12px;
  text-align: center;
}

tr:nth-child(even), {
  background-color:;
}
.veinte {
  list-style-type: none;
  margin:;
  padding:;
  overflow: hidden;
  background-color:rgb(60,60,60);
  
}
button, {
    align:center;
    right: 20px;
border-radius: 10px;
align:center;
}

.btn{
        margin: 0px; 
    border:0px; 
    display: block; 
    margin: auto; 
    padding: 10px 30px;
    background: #333;
    color:#fff;
    border-radius: 5px;
    margin-bottom: 10px;
  background-color: #FF4343;
   color: black;
}
</style>