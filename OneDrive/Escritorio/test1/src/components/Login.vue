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
      usuario: "",
      password: ""
    }
  },
  methods:{
    login(){
      // eslint-disable-next-line
      console.log("Entrar");
      axios.post('http://localhost:3000/login',{
          username:this.usuario,
          password:this.password
      })
      .then(response => {
        console.log(response.data)
        if (response.data == "ok"){
          this.$emit('click_login');
        }
        else if(response.data == "no"){
          console.log('usuario o contraseña incorrectas')
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

html,body{ padding: 0px; margin: 0px; width: 100%; height: 100vh; font-family: "Roboto"; color:#333;  }
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
