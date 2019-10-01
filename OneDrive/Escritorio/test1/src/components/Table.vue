<template>
    <div>
    <button @click="logout()">Logout</button>
<table border="1" align="center"  bordercolor="white" cellspacing="0">
    <th width="200" height="30" bgcolor="48A5E6">
        IdEmpleado
        </th>
        <th width="200" height="30" bgcolor="48A5E6" >
        nombre
        </th>
         <th width="200" height="30" bgcolor="48A5E6">
        apellido
        </th>
         <th width="200" height="30" bgcolor="48A5E6">
        dpi
        </th>
         <th width="200" height="30" bgcolor="48A5E6">
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
        <td>
        <button class="btn" @click="deleteEmpleado(todo.idEmpleado)">Borrar</button>
        </td>
            </tr>
     </table>
     <div class="divlogin">
       <div class="container">
       <div class="divcont">
     <input type="text" name="Nombre" v-model="nombre" placeholder="Nombre"/>
     <input type="text" name="Apllido" v-model="apellido" placeholder="Apellido" />
    <input type="text" name="DPI" v-model="dpi" placeholder="DPI"/>
    <input type="email" name="Email" v-model="email" placeholder="Email" />
    <button @click="agregar()">Enviar</button>
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
            nombre:"",
            apellido:"",
            dpi:"",
            email:"",
        }
    }, 
    mounted (){
        this.getTodos();
    }   ,
    methods:{
        logout(){
          $IdEmpleado = $_POST['IdEmpleado'];
          $Nombre = $_POST['Nombre'];
          $Apellido = $_POST['Apellido'];
          $DPI = $_POST['DPI'];
          $Email= $_POST['Email'];

            this.$emit("logout");
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
        agregar(){
             axios.post('http://localhost:3000/agregarEmpleado',{
          nombre:this.nombre,
          apellido:this.apellido,
          dpi:this.dpi,
          email:this.email
            })
            .then(response => {
                this.getTodos()
                console.log(response.data)
            }).catch(e => {
                console.log(e)
            })
        },
        deleteEmpleado(idEmpleado){
             axios.delete('http://localhost:3000/eliminarEmpleado/'+ idEmpleado)
            .then(response => {
                this.getTodos();
                console.log(response.data)
            }).catch(e => {
                console.log(e)
            })
        }
    }
}
</script>
<style>
html, body { background: gray; padding: 0px; margin: 0px; width: 100%; height: 100vh; font-family: "Roboto"; color:#333;  }
.divlogin{ 
  background: gray;
    background-size: cover; 
    background-position: center center; 
    width: 100%; 
    height: 100vh; 
    display: flex;
    align-content: center;
    align-items: center;    
}
.divlogin .container{ 
    width: 100%;
    text-align: center;
}
.divlogin .container .divcont{
    width: 100%;
    max-width: 300px;
    background: rgba(255,255,255,0.7);
    padding: 20px;
    border-radius: 10px;
    display: inline-block;
}
.divlogin .container .divcont h3{
    margin-top: 0px;
}
.divlogin .container .divcont input{ 
    height: 30px; 
    margin: 0px; 
    border: 0px; 
    outline: none; 
    padding: 10px; 
    border-radius: 5px; 
    width: 90%;
    margin-bottom: 10px;
}
.divlogin .container .divcont input.error,
.divlogin .container .divcont button{ 
    margin: 0px; 
    border:0px; 
    display: block; 
    margin: auto; 
    padding: 10px 30px;
    background: #333;
    color:#fff;
    border-radius: 5px;
    margin-bottom: 10px;
}
.divlogin .container .btn .divcont a{
    font-size: 12px;
    margin-right: 10px;
    color:#333;
}


</style>