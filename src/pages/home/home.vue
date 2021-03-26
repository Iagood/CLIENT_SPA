<template>
  <siteTemplate>
    <span slot="menuesquerdo">
      <div class="row valign-wrapper">
        <grade tamanho="4">
          <img
            :src="usuario.imagem"
            :alt="usuario.name"
            class="circle responsive-img"
          />
          <!-- notice the "circle" class -->
        </grade>
        <grade tamanho="8">
          <span class="black-text">
            <h5>{{ usuario.name }}</h5>
            Developer
          </span>
        </grade>
      </div>
    </span>
    <span slot="principal">
      <publicarConteudo />

      <cartaoConteudo v-for="item in listaConteudos" :key="item.id"
        :id="item.id"
        :perfil="item.user.imagem"
        :nome="item.user.name"
        :data="item.data">
        
        <cartaoDetalhe
          :img="item.imagem"
          :titulo="item.titulo"
          :txt="item.texto"
          :link="item.link"  
        />
      </cartaoConteudo>
    </span>
  </siteTemplate>
</template>
<script src="https://cdn.jsdelivr.net/npm/sweetalert2@9"></script>
<script>
import publicarConteudo from "@/components/social/publicarConteudo";
import cartaoConteudo from "@/components/social/cartaoConteudo";
import cartaoDetalhe from "@/components/social/cartaoDetalhe";
import grade from "@/components/layout/grade";
import siteTemplate from "@/templates/siteTemplate";

export default {
  name: "Home",
  data() {
    return {
      usuario: false
    };
  },
  created() {
    let usuarioAux = this.$store.getters.getUsuario;
    if (usuarioAux) {
      this.usuario = this.$store.getters.getUsuario;
      this.$http
        .get(
          this.$urlAPI+`conteudo/listar`,
          {
            headers: {
              authorization: "Bearer " + this.$store.getters.getToken,
            },
          }
        )
        .then((response) => {
         console.log(response.data)
         if(response.data.status){
            this.$store.commit('setConteudosLinhaTempo',response.data.conteudos.data)
         }
          
        })
        .catch((e) => {
          console.log(e)
          alert("Erro! Tente novamente mais tarde!");
        });
    }
  },
  components: {
    cartaoConteudo,
    cartaoDetalhe,
    grade,
    publicarConteudo,
    siteTemplate,
  },
  computed:{
    listaConteudos(){
      return this.$store.getters.getconteudosLinhaTempo;
    }
  }
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>
