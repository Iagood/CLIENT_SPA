<template>
  <span>
    <header>
      <navbar url="#/" cor="teal darken-2" logo="Social">
          <li><a href="#/">Home</a></li>
          <li><a href="#/login">Entrar</a></li>
      </navbar>
    </header>
    <main>
      <div class="container">
        <div class="row">
          <grade tamanho="4">
              <cartaomenu>
                  <slot name="menuesquerdo"/>
              </cartaomenu>
              <cartaomenu>
                <h3>Teste</h3>
              </cartaomenu>  
          </grade>
          <grade tamanho="8">
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
  name: "siteTemplate",
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
