<template>
  <span>
    <header>
      <navbar cor="teal darken-2" logo="Social" />
    </header>
    <main>
      <div class="container">
        <div class="row">
          <grade tamanho="6">
              <slot name="menuesquerdo"/>
              
          </grade>
          <grade tamanho="6">
           <slot name="principal"/>
          </grade>
        </div>
      </div>
    </main>
    <rodape cor="teal darken-2" logo="Social" descricao="Teste de descricao" ano="2021">
      <li><a class="grey-text text-lighten-3" href="#!">Home</a></li>
      <li><a class="grey-text text-lighten-3" href="#!">Link 2</a></li>
      <li><a class="grey-text text-lighten-3" href="#!">Link 3</a></li>
      <li><a class="grey-text text-lighten-3" href="#!">Link 4</a></li>
    </rodape>
  </span>
</template>

<script>
import navbar from "@/components/layout/navbar";
import rodape from "@/components/layout/rodape";
import grade from "@/components/layout/grade";
import cartaomenu from "@/components/layout/cartaomenu";
import cartaoConteudo from "@/components/social/cartaoConteudo";


export default {
  name: "loginTemplate",
  components: {
    navbar,
    rodape,
    grade,
    cartaomenu,
    cartaoConteudo
  },
};
</script>

<style>
</style>
