<html>
<body>
<p>
<img src="/assets/{{Esource.png}}" class="img-responsive" height="70" width="90">
</p>
</body>
   </html>
<template>
  <div id="login">
  <div class="divlogin">
        <div class="container">
            <div class="divcont">
    <label>Usuario:</label> 
    <input type="text" name="Usuario" v-model="usuario" placeholder="Usuario" />
    <br>
    <label>Contraseña:</label> 
    <input type="password" name="password" v-model="password" placeholder="Password" />
    <button @click="login()">Entrar</button>
    <label v-if="response==1">
     Usuario y/o Contraseña incorrecta
    </label>
  </div>
  </div>
  </div>
  </div>

</template>

<script>
import axios from 'axios'
export default {
  name: 'Login',
  data(){
    return {
      response:"",
      usuario: "",
      password: ""
    }
  },
  methods:{
    login(){
      // eslint-disable-next-line
      console.log("Entrar");
      axios.post('http://localhost:3000/login',{
          usuario:this.usuario,
          password:this.password
      })
      .then(response => {
        // eslint-disable-next-line 
        console.log(response.data)
        if (response.data == "ok"){
          this.$emit('click_login');
        }
        else if(response.data == "error"){
          // eslint-disable-next-line 
          this.response=1
        }
      }).catch(e => {
      this.errors.push(e)
    })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.googleapis.com/css?family=Roboto');

html,body{ background: white; padding: 0px; margin: 0px; width: 100%; height: 100vh; font-family: "Roboto"; color:black;  }
.divlogin{ 
  background:white ;
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
    max-width: 10%;
    background: #black;
    padding: 5%;
    border-radius: 5%;
    display: inline-block;
}
.divlogin .container .divcont h3{
    margin-top: 0px;
}
.divlogin .container .divcont input{ 
    height: 15%; 
    margin: 0px; 
    border: 0px; 
    outline: none; 
    padding: 10%; 
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
    background: black;
    color:;
    border-radius: 5px;
    margin-bottom: 10px;
}
.divlogin .container .divcont a{
    font-size: 12px;
    margin-right: 10px;
    color:black;
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
