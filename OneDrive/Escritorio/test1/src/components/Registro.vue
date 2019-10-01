<template>
<div class="divlogin">
       <div class="container">
       <div class="divcont">
     <input type="text" name="Nombre" v-model="nombre" placeholder="Nombre"/>
     <input type="text" name="Apllido" v-model="apellido" placeholder="Apellido" />
    <input type="number" name="DPI" v-model="dpi" placeholder="DPI"/>
    <input type="email" name="Email" v-model="email" placeholder="Email" />
    <button id="1" @click="cancelar()">Cancelar</button>
    <button id="2" @click="agregar()">Enviar</button>
    </div>
    </div>
    </div>
</template>

<script>
import axios from 'axios'
export default {
    name: 'Registro',
    data(){
        return{
            nombre:"",
            apellido:"",
            dpi:"",
            email:"",
        }
    }, 
    mounted (){
    }   ,
    methods:{
        cancelar(){
            this.$emit("cancelar");
        },
        agregar(){
           this.$emit("agregar");
             axios.post('http://localhost:3000/agregarEmpleado',{
          nombre:this.nombre,
          apellido:this.apellido,
          dpi:this.dpi,
          email:this.email
            })
            .then(response => {
               // this.getTodos()
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
html, body { background: gray; padding: 0px; margin: 0px; width: 100%; height: 100vh; font-family: "Roboto"; color:#333;  }
.divlogin { 
  background: gray;
    background-size: ; 
    background-position:  center; 
    width: 100%; 
    height: 100vh; 
    display: flex;
    align-content: ;
    align-items:;
    
}
.divlogin .container { 
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