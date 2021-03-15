<template>
  <loginTemplate>
    <h2>Login</h2>
    <span slot="menuesquerdo">
      <img
        src="https://png.pngtree.com/png-vector/20191003/ourmid/pngtree-user-login-or-authenticate-icon-on-gray-background-flat-icon-ve-png-image_1786166.jpg"
        alt=""
        class="circle responsive-img"
      />
    </span>
    <span slot="principal">
      <span>
        <h4>Login</h4>
        <input type="text" placeholder="E-mail" v-model="email"/>
        <input type="password" placeholder="Senha" v-model="password" />
        <button v-on:click="login" class="btn">Entrar</button>
        <router-link to="/cadastro" class="btn orange">Cadastre-se</router-link>
      </span>
    </span>
  </loginTemplate>
</template>

<script>
import loginTemplate from "@/templates/loginTemplate";
import axios from "axios";

export default {
  name: "Login",
  data() {
    return {
      email:'',
      password:''
    };
  },
  components: {
    loginTemplate,
  },
  methods: {
    login() {
      axios
        .post('http://127.0.0.1:8000/api/login', {
          email: this.email,
          password: this.password
        })
        .then((response) => {
          // console.log(response);
          if(response.data.token){
            console.log('Login com sucesso');
            //Criar sessão que pegue um item json e transforme em string.
            sessionStorage.setItem('usuario',JSON.stringify(response.data));
            this.$router.push('/');

          }
          else if(response.data.status == false){ 
           console.log('Login não existe');
           alert('Login inválido!');   
          }
          else{
            console.log('Erro na validação');
            let erros ='';
            for(let erro of Object.values(response.data)){
              erros += erro + ' ';
            }
            alert(erros);
          }
        })
        .catch((e) => {
          
        });
    },
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>
