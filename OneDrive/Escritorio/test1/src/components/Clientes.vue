<template>
   <div id="login">
  <div class="divlogin">
        <div class="container">
            <div class="divcont">
 <input type="number" name="id" v-model="id" placeholder="ID" />
    <input type="number" name="fecha" v-model="dias" placeholder="Dias" />
    <table>
    <td>
    <button @click="enviar()">Registrar</button>   
    </td>
    <td>  
     <button @click="regresar()">Regresar</button>  
    </td>
    </table>
    </div>
    </div>    
 </div>
    </div>

</template>
<script>
import axios from 'axios'
export default {
     name: 'Clientes',
    data(){
        return{
            id:"",
            nombre:"",
            apellido:"",
            email:"",
            dias:"",

        }
    }, 
    methods:{
        regresar(){
            this.$emit("regresar");
        },
         enviar(){           
          if(this.id==""|| this.dias==""  ){
              // eslint-disable-next-line
              console.log('rellena todos los campos')
          }else{
          this.$emit("enviar");
          axios.post('http://localhost:3000/crearSolicitud/'+this.id,{
          nombre:this.nombre,
          apellido:this.apellido,
          email:this.email,
          dias:this.dias
            })
           .then(response => {
        // eslint-disable-next-line
        console.log(response.data)
      }).catch(e => {
      this.errors.push(e)
    })           
        }
      }
    }
}
</script>
<style>
html,body{ padding: 0px; margin: 0px; width: 100%; height: 100vh; font-family: "Roboto"; color:#333;  }
.divlogin{ 
  background: black;
    background-size: cover; 
    background-position: center center; 
    width: 100%; 
    height: 100vh; 
    display: flex;
    align-content: center;
    align-items: center;    
}
.divlogin .container { 
    width: 100%;
    text-align: center;
}
.divlogin .container .divcont{
    width: 100%;
    max-width: 300px;
    background: green;
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
.divlogin .container .divcont a{
    font-size: 12px;
    margin-right: 10px;
    color:#333;
}
h3 {
  margin: 40px 0 0;
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