<template>
  <siteTemplate>
    <span slot="menuesquerdo">
         <div class="row valign-wrapper">
            <grade tamanho="4">
              <img
                src="https://developers.google.com/web/images/contributors/no-photo.jpg"
                alt=""
                class="circle responsive-img"
              />
              <!-- notice the "circle" class -->
            </grade>
            <grade tamanho="8">
              <span class="black-text">
                <h5>Iago Barbosa</h5>
                Developer
              </span>
            </grade>
          </div>
    </span> 
    <span slot="principal">
       <publicarConteudo/>
  
    <cartaoConteudo
      perfil="https://developers.google.com/web/images/contributors/no-photo.jpg"
      nome="Iago Barbosa"
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
      msg: "Estudando Vue.js",
    };
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
