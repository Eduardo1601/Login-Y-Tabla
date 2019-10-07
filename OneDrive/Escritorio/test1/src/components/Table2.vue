<template>
    <div>
      <h1>SOLICITUDES</h1>
    <div class="dis">
    <div class="login">
       <div class="tainer">
       <div class="veinte">
     <table>
          <th>
              <div>
          <button  class="celula" @click="regresar()">Regresar</button>
          </div>
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

        
    <tr v-for="todo in todos" :key="todo.id">
        
        <td bgcolor="82E0AA" > {{todo.id}}
        </td>
         <td bgcolor="#C5C3C3">{{todo.empleado.nombre}}
        </td>
        <td bgcolor="#C5C3C3">{{todo.empleado.apellido}}
        </td>
        <td bgcolor="#C5C3C3">{{date(todo.fecha)}}
        </td>
        <td bgcolor="#C5C3C3">{{todo.diasSolicitados}}
        </td>
        <td bgcolor="#C5C3C3">{{todo.status}}
        </td>
        <td>
        <button class="btn" @click="deleteSolicitud(todo.id)">Borrar</button>
        </td>
        <td>
        <button class="btn" @click="aceptar(todo.id)" v-if="todo.status=='pendiente'">Aceptar</button>
        </td>
        <td>
        <button class="btn" @click="rechazar(todo.id)" v-if="todo.status=='pendiente'">Rechazar</button>
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
          id:"",
            todos:null,
            status:0,
            boton:0
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
        },
        aceptar(id){
          const config = { headers: {'Content-Type': 'application/json'} };
          axios.post('http://localhost:3000/estado/'+id,{
            status:"aceptado"
            })
            .then(response => {
               // this.getTodos()
               // eslint-disable-next-line
               this.getTodos();
                console.log(response.data)
                this.boton=1
                this.$emit("aceptar");
            }).catch(e => {
                // eslint-disable-next-line 
                console.log(e)
            })
        },
        rechazar(id){
          axios.post('http://localhost:3000/estado/'+id,{
            status:"rechazado"
            })
            .then(response => {
               // this.getTodos()
               // eslint-disable-next-line
               this.getTodos()
                console.log(response.data)
                this.boton=1
                this.$emit("aceptar");
            }).catch(e => {
                // eslint-disable-next-line 
                console.log(e)
            })
        }      
    }
 }
</script>

<style>
button, th, td, .celula {
    align:center;
    right: 20px;
border-radius: 0px;
align:center;
}


.celula{
  border: 0px solid #dddddd;
  text-align: right;
  padding: 12px;
  border-radius: 5px;
  text-align: center;
  font-family: Tahoma;
  font-size: 20px;
background: #82E0AA ;
  display: block;
  color: ;
  text-align: center;
  padding: ;
  text-decoration: none;
}

.cuatro {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color:;
}

td, th, table{
  border: 0px solid #dddddd;
  text-align: left;
  padding: 12px;
  text-align: center;
}

tr:nth-child(even), .tres{
  background-color: ;
}
.cuatro {
  list-style-type: none;
  margin: 0;
  padding: 0;
  overflow: hidden;
  background-color: ;
}

.cuatro {
  float: center;
}


button a:hover {
  background-color: ;
}

body {margin:0;}

  .cuatro {
  list-style-type: none;
  margin:;
  padding:;
  overflow: hidden;
  background-color:;
  position:fixed;
  top: 0;
  width: 75%;
}

button {
  float: left;
}

.cuatro button{
  display: block;
  color: ;
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
  background-color:;
  
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
    background: ;
    color:;
    border-radius: 5px;
    margin-bottom: 10px;
  background-color: #FF4343;
   color: ;
}
</style>