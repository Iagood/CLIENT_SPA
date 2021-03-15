<template>
  <siteTemplate>
    <span slot="menuesquerdo">
         <div class="row valign-wrapper">
            <grade tamanho="4">
              <img :src="usuario.imagem" :alt="usuario.name" class="circle responsive-img"/>
              <!-- notice the "circle" class -->
            </grade>
            <grade tamanho="8">
              <span class="black-text">
                <h5>{{usuario.name}}</h5>
                Developer
              </span>
            </grade>
          </div>
    </span> 
    <span slot="principal">
       <publicarConteudo/>
  
    <cartaoConteudo
      :perfil="usuario.imagem"
      :nome="usuario.name"
      data="05/03/2021">
    
      <cartaoDetalhe
        img="https://miro.medium.com/max/2560/1*Ht8T-vqbqy5iG7FzNQGjFA.png"
        txt="Vue JS é um framework Javascript open source, lançado em Fevereiro de 2014 por Evan You,
      Desenvolvedor que atuava em um dos projetos do Google Creative Labs, em 2014."
        titulo="SPA com Vue.js"/>
    </cartaoConteudo>
      
    </span>  
  </siteTemplate>
</template>

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
    let usuarioAux = sessionStorage.getItem("usuario");
    if (usuarioAux) {
      this.usuario = JSON.parse(usuarioAux);
  
    }
  },
  components: {
    cartaoConteudo,
    cartaoDetalhe,
    grade,
    publicarConteudo,
    siteTemplate
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>
