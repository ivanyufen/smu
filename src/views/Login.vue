<template>
  <div class="home">
    <img alt="paket logo" class="logo" src="../assets/paketid.png">
    <h1>SMU LOGIN</h1>
    
    <md-card>
      <md-card-content>
        <div class="md-layout md-alignment-center-center">
          <md-field :class="{'md-invalid' : emailEmpty}">
            <md-icon>account_circle</md-icon>
            <label>Email / Username</label>
            <md-input v-model="user.email" @keydown.enter="handleLogin"></md-input>
            <span class="md-error">Email must be filled</span>
          </md-field>
          <br />
          <md-field :class="{'md-invalid' : passwordEmpty}">
            <md-icon>lock</md-icon>
            <label>Password</label>
            <md-input type="password" v-model="user.password" @keydown.enter="handleLogin"></md-input>
            <span class="md-error">Password must be filled</span>
          </md-field>
        </div>
      </md-card-content>
    </md-card>
    
    <div class="md-layout md-alignment-center-center">
      <md-button class="md-raised md-primary" @click="handleLogin" :disabled="btnLoginDisabled">Login</md-button>
    </div>

    <!-- footer -->
    <p class="md-caption">Copyright &copy PT Paket Informasi Digital 2019</p>

  </div>
</template>

<script>
import axios from 'axios';
import URL from '@/endpoint.js';

export default {
  name: 'login',
  components: {
    
  },
  data(){
    return {
      user: {
        email: '',
        password: ''
      },
      emailEmpty: false,
      passwordEmpty: false,
      btnLoginDisabled: false
    }
  },
  methods: {
    handleLogin(){
      // validate if user fill email and password
      if(!this.user.email){
        this.emailEmpty = true;
        return;
      }
      else{
        this.emailEmpty = false;
      }
      if(!this.user.password){
        this.passwordEmpty = true;
        return;
      }
      else{
        this.passwordEmpty = false;
      }
      // end of validate

    // login process
    this.btnLoginDisabled = true;
    axios.post(URL.login, JSON.stringify({email: this.user.email, password: this.user.password}))
      .then((res) => {
        console.log(res)
        this.btnDisabled = false;
      })
      .catch((err) => {
        console.log(err, "Error")
        this.btnDisabled = false;
      })
      // end of login process
    }
  }
}
</script>

<style lang="scss" scoped>

.md-button{
  width: 320px !important;
  border-radius: 10px;
}
  .md-card {
    width: 320px;
    margin: 4px;
    display: inline-block;
    vertical-align: top;
    border-radius: 10px;
  }
</style>

<style scoped>
  .logo{
    margin: 2em auto;
  }
</style>