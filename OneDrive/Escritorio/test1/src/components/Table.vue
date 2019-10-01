<template>
    <div>
   <button @click="Refrescar()">Refrescar</button>
 <button @click="logout()">Logout</button>
    <button @click="nuevo()">nuevo</button>
<table border="1" align="center"  bordercolor="white" cellspacing="0">
    <th class="volor" width="150" height="30" bgcolor="48A5E6">
        IdEmpleado
        </th>
        <th class="volor" width="150" height="35" bgcolor="48A5E6" >
        nombre
        </th>
         <th class="volor" width="150" height="35" bgcolor="48A5E6">
        apellido
        </th >
         <th class="volor" width="150" height="35" bgcolor="48A5E6">
        dpi
        </th>
         <th class="volor" width="150" height="35" bgcolor="48A5E6">
        email
        </th>

        
    <tr v-for="todo in todos" :key="todo.idEmpleado">
        
        <td bgcolor="D8EFFF" > {{todo.idEmpleado}}
        </td>
         <td bgcolor="91D6F1">{{todo.nombre}}
        </td>
        <td bgcolor="D8EFFF">{{todo.apellido}}
        </td>
        <td bgcolor="91D6F1">{{todo.dpi}}
        </td>
        <td bgcolor="D8EFFF">{{todo.email}}
        </td>
        <td class="btn">
        <button class="btn" @click="deleteEmpleado(todo.idEmpleado)">Borrar</button>
        </td>     
            </tr>
     </table>
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