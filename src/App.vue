<template>
  <body>
    <main>
      <div class="container">
        <div class="row">
          <div class="col">
            <img alt="login" class="img-fluid" src="./assets/images/login-img.png" width="500" height="500" />
          </div>
          <div class="box col">
            <div class="container">
              <div class="row">
                <div class="col">
                  <div class="logo text-center">
                    <img alt="logo" class="img-fluid" src="./assets/images/illarli-logo-black.svg"/>
                  </div>
                </div>
              </div>
              <div class="row">
                <div class="col">
                  <div class="text-center">
                    <h2 class="title"><b>Iniciar Sesión</b></h2>
                    <span class="title">En el <b>sistema de facturación</b> que se adapta a tus necesidades</span>
                  </div>
                </div>
              </div>
              <div class="space row">
                <div class="col">
                  <form v-on:submit.prevent="login">
                    <div class="form-group">
                      <label for="inputUser">Usuario</label>
                      <input type="text" class="form-control" id="inputUser" aria-describedby="emailHelp" placeholder="Usuario" v-model="user">
                    </div>
                    <div class="form-group">
                      <label for="inputPassword">Contraseña</label>
                      <input type="password" class="form-control" id="inputPassword" placeholder="Contraseña" v-model="password">
                    </div>
                    <div class="container">
                      <div class="row">
                        <div class="col-5">
                          <div class="form-check">
                            <input type="checkbox" class="form-check-input" id="exampleCheck1">
                            <label class="form-check-label" for="exampleCheck1">Recordarme</label>
                          </div>
                        </div>
                        <div class="col hyperlinks">
                          ¿Olvidaste tu contraseña?
                        </div>
                      </div>
                    </div>
                    <div class="text-center">
                      <button type="submit" class="btn btn-primary main-button">Acceder</button>
                    </div>
                  </form>
                </div>
              </div>
              <div class="row text-center">
                <div class="col">
                  ¿No tienes cuenta?
                </div>
                <div class="col hyperlinks">
                  Regístrate aquí
                </div>
              </div>
            </div>
          </div>
        </div>
      </div>      
    </main>
  </body>
</template>
<style>
body {
background-image: url('./assets/images/background-auth.jpg');
}
main{
  margin-top: 10%;
  margin-bottom: 10%;
}
.box{
  background-color: #e7e7e7;
  border-radius: 10%;
}
.logo{
  margin-top: 5%;
  margin-bottom: 5%;
}
.title
{
  color: #120b39;
  font-family: Arial, Helvetica, sans-serif;
}
.space{
  margin: 5%;
}
.main-button{
  margin-top: 5%;
  width: 100%;
}
.hyperlinks{
  color: #120b39;
  font-family: Arial, Helvetica, sans-serif;
  text-decoration: underline;
  font-weight: bold;
}
</style>
<script>
import axios from 'axios'

export default {
  name: 'App',
  components:{

  },
  data: function(){
    return {
      user:"",
      password:"",
      error:false,
      error_msg:""
    }
  },
  methods:{
    login(){
      let json={
        "email": this.user,
        "password": this.password
      };
      var bodyFormData = new FormData (); 
      bodyFormData.append("email", this.user);
      bodyFormData.append("password", this.password); 
      axios.post('https://eventos.ec/api/login',bodyFormData)
      .then(data=>{
        console.log(data);
      })
    }
  },
  mounted() {
    axios.get('https://eventos.ec/api/categories', {
    headers: {
      'Accept': 'application/json',
      'Authorization': 'Bearer ' + "1|IOuQ36x8QS32tbuMCkvA4RjsJ0n2zJlyrfUDBiVn"
    }
  })
  .then(response => {
    console.log(response.data);
    // Aquí puede hacer algo con los datos de la respuesta
  })
  .catch(error => {
    console.log(error);
  });
  }
}
</script>