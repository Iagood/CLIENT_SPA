<template>
  <siteTemplate>
    <h2>Login</h2>
    <span slot="menuesquerdo">
      <img
        :src="usuario.imagem"
        alt=""
        class="circle responsive-img"
      />
    </span>
    <span slot="principal">
      <span>
        <h4>Perfil</h4>

        <input type="text" placeholder="Nome" v-model="name" />
        <input type="text" placeholder="E-mail" v-model="email" />

        <p>
           <div class="file-field input-field">
              <div class="btn">
                <span>imagem</span>
                <input @change="salvaImagem" type="file">
              </div>
            <div class="file-path-wrapper">
              <input class="file-path validate" type="text">
            </div>
          </div>

        </p>
        <img class="image"/>

        <input type="password" placeholder="Senha" v-model="password" />
        <input
          type="password"
          placeholder="Confirme sua senha"
          v-model="password_confirmation"
        />
        <button class="btn" v-on:click="perfil()">Atualizar</button>
      </span>
    </span>
  </siteTemplate>
</template>

<script>
import siteTemplate from "@/templates/siteTemplate";
import axios from "axios";

export default {
  name: "Perfil",
  data() {
    return {
      usuario: false,
      name: "",
      email: "",
      imageSrc: "",
      password: "",
      password_confirmation: "",
    };
  },
  components: {
    siteTemplate,
  },
  methods: {
    salvaImagem: function (e) {
      var file = document.querySelector("input[type=file]").files[0];

      if (e.target.files[0]) {
        var reader = new FileReader();

        reader.onload = (e) => {
          this.imageSrc = e.target.result;
        };
      }
      reader.readAsDataURL(file);
    },
    perfil() {
      axios
        .put(
          "http://127.0.0.1:8000/api/perfil",
          {
            name: this.name,
            email: this.email,
            imagem: this.imageSrc,
            password: this.password,
            password_confirmation: this.password_confirmation,
          },
          { headers: { authorization: "Bearer " + this.usuario.token } }
        )
        .then((response) => {
          console.log(response);
          if (response.data.token) {
            console.log(response.data);
            this.usuario = response.data;
            sessionStorage.setItem("usuario", JSON.stringify(this.usuario));
            alert("Perfil atualizado!");
          } else if (response.data.status == false) {
            alert("Erro,tente novamente mais tarde!");
          } else {
            console.log("Erro na validação");
            let erros = "";
            for (let erro of Object.values(response.data)) {
              erros += erro + " ";
            }
            alert(erros);
          }
        })
        .catch((e) => {});
    },
  },
  created() {
    let usuarioAux = sessionStorage.getItem("usuario");
    if (usuarioAux) {
      this.usuario = JSON.parse(usuarioAux);
      this.name = this.usuario.name;
      this.email = this.usuario.email;
    }
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>
