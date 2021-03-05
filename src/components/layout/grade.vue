<template>
    <div :class="'col s'+tamanho">
        <slot></slot>
    </div>
    
</template>

<script>
export default {
  name: "grade",
  props: ['tamanho'],
  data() {
    return {};
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>