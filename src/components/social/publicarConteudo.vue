<template>
    <span>
        <div class="row">
            <grade class="input-field" tamanho="12">
            <textarea v-model="conteudo" id="conteudo" class="materialize-textarea"></textarea>
            <label for="conteudo">O que está acontecendo?</label>
            </grade>
            <p>
            <grade v-if="conteudo" class="btn waves-effect waves-light" tamanho="2 offset-s10"
                >Publicar</grade>
            </p>
        </div>
    </span>
</template>

<script>
import grade from "@/components/layout/grade";
export default {
  name: "publicarConteudo",
  props: [],
  data() {
    return {
        conteudo:''
    };
  },
  components: {
    grade,
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>