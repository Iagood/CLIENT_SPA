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
        <h4>Cadastro</h4>

        <input type="text" placeholder="Nome" v-model="name" />
        <input type="text" placeholder="E-mail" v-model="email" />
        <input type="password" placeholder="Senha" v-model="password" />
        <input
          type="password"
          placeholder="Confirme sua senha"
          v-model="password_confirmation"
        />
        <button class="btn" v-on:click="cadastro()">Enviar</button>
        <router-link to="/login" class="btn orange">Já tenho conta</router-link>
      </span>
    </span>
  </loginTemplate>
</template>

<script>
import loginTemplate from "@/templates/loginTemplate";

export default {
  name: "Cadastro",
  data() {
    return {
      name: "",
      email: "",
      password: "",
      password_confirmation: "",
    };
  },
  components: {
    loginTemplate,
  },
  methods: {
    cadastro() {
      this.$http
        .post("http://127.0.0.1:8000/api/cadastro", {
          name: this.name,
          email: this.email,
          password: this.password,
          password_confirmation: this.password_confirmation,
        })
        .then((response) => {
          // console.log(response);
          if (response.data.status) {
            console.log("Cadastrado com sucesso!");
            this.$store.commit('setUsuario',response.data.usuario)
            //Criar sessão que pegue um item json e transforme em string.
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
            alert("Erro,tente novamente mais tarde!");
          }
        })
        .catch((e) => {
          console.log("nada");
        });
    },
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>
