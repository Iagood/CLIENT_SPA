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
        <input type="text" placeholder="E-mail" v-model="email" />
        <input type="password" placeholder="Senha" v-model="password" />
        <button v-on:click="login" class="btn">Entrar</button>
        <router-link to="/cadastro" class="btn orange">Cadastre-se</router-link>
      </span>
    </span>
  </loginTemplate>
</template>
<script src="//cdn.jsdelivr.net/npm/sweetalert2@10"></script>
<script>
const Swal = require("sweetalert2");
import loginTemplate from "@/templates/loginTemplate";

export default {
  name: "Login",
  data() {
    return {
      email: "",
      password: "",
    };
  },
  components: {
    loginTemplate,
  },
  methods: {
    login() {
      this.$http.post(this.$urlAPI+`login`, {email: this.email,password: this.password,})
        .then((response) => {
          console.log(response);
          if (response.data.status) {
            console.log("Login com sucesso");
            //Criar sessão que pegue um item json e transforme em string.
            this.$store.commit('setUsuario',response.data.usuario)
            sessionStorage.setItem("usuario", JSON.stringify(response.data.usuario));
            this.$router.push("/");
          } else if (response.data.status == false && response.data.validacao) {

              console.log("Erro na validação");
              let erros = "";
              for (let erro of Object.values(response.data.erros)) {
                erros += erro + " ";
              }
              alert(erros);

          } else {
           
            console.log("Login não existe");
            alert("Login inválido!");
          }
        })
        .catch((e) => {
          alert(e);
        });
    },
  },
  beforeDestroy() {
    let usuarioAux = sessionStorage.getItem("usuario");
    this.usuario = JSON.parse(usuarioAux);

    Swal.fire({
      position: "top-center",
      icon: "success",
      title: "Bem vindo "+this.usuario.name,
      showConfirmButton: false,
      timer: 1500,
    });
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>
