<template>
  <span>
    <div v-if="img" class="card-image">
      <img :src="img"/>
      <span class="card-title">{{titulo || 'Título genérico' }}</span>
    </div>

    <div v-if="txt" class="card-content">
      <p>{{txt}}</p>
    </div>
  </span>
</template>

<script>

export default {
  name: "cartaoDetalhe",
  props: ['img','titulo','txt'],
  data() {
    return {};
  },
  components: {

  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>