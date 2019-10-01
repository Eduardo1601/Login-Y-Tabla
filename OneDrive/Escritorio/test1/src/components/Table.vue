<template>
    <div>
    <div class="dis">
   <button @click="Refrescar()">Refrescar</button>
 <button @click="logout()">Logout</button>
    <button @click="nuevo()">nuevo</button>
<table border="1" align="center"  bordercolor="6F6F6F" cellspacing="0">
    <th class="volor" width="150" height="30" bgcolor="FFFFFF">
        IdEmpleado
        </th>
        <th class="volor" width="150" height="35" bgcolor="FFFFFF" >
        nombre
        </th>
         <th class="volor" width="150" height="35" bgcolor="FFFFFF">
        apellido
        </th >
         <th class="volor" width="150" height="35" bgcolor="FFFFFF">
        dpi
        </th>
         <th class="volor" width="150" height="35" bgcolor="FFFFFF">
        email
        </th>

        
    <tr v-for="todo in todos" :key="todo.idEmpleado">
        
        <td bgcolor="E5DCDC" > {{todo.idEmpleado}}
        </td>
         <td bgcolor="CCC9C9">{{todo.nombre}}
        </td>
        <td bgcolor="E5DCDC">{{todo.apellido}}
        </td>
        <td bgcolor="CCC9C9">{{todo.dpi}}
        </td>
        <td bgcolor="E5DCDC">{{todo.email}}
        </td>
        <td class="btn">
        <button class="btn" @click="deleteEmpleado(todo.idEmpleado)">Borrar</button>
        </td>     
            </tr>
            
     </table>
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
        getTodos(){
            axios 
            .get('http://localhost:3000/prueba',{
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




.dis{

 width: 100%;
    max-width: 1000px;
    background: rgba(255,255,255,0.7);
    padding: 20px;
    border-radius: 10px;
    display: inline-block;
    
}





</style>