<template>
<div class="row">
  <div class="card">
    <div class="card-content">
      <div class="row valign-wrapper">
        <grade tamanho="1">
          <img :src="perfil" :alt="nome" class="circle responsive-img"/>
          <!-- notice the "circle" class -->
        </grade>
        <grade tamanho="11">
          <span class="black-text">
            <strong>{{nome}}</strong> - <small>{{data}}  11:37</small>
          </span>
        </grade>
        
      </div>

      <slot/>
      <div class="card-action">
        <p>
          <i class="material-icons">favorite_border</i>
          <i class="material-icons">insert_comment</i>
        </p>  
      </div>
    </div>
  </div>
  </div>
</template>

<script>
import grade from "@/components/layout/grade";
export default {
  name: "cartaoConteudo",
  props: ['perfil','nome','data'],
  data() {
    return {};
  },
  components: {
      grade
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>