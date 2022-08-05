<template>
  <div id="app">
    <form>
      <input type="text" v-model="us_login" />
      <input type="password" v-model="us_senha" />
      <button type="submit" @click.prevent="send">Enviar</button>
    </form>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: 'App',
  data() {
    return {
      us_login: '',
      us_senha: '',
    }
  },
  methods: {
    send() {
      console.log(this.us_login, this.us_senha);
      axios.post(
        'http://localhost:8081/auth/login', 
        {
          "us_login": this.us_login,
          "us_senha": this.us_senha
        }
      )
        .then(response => console.log(response))
        .catch(error => console.log(error));
    }
  }  
}
</script>

