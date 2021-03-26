<template>
    <span>
        <div class="row">
            <grade class="input-field" tamanho="12">
            <input id="titulo" type="text" v-model="conteudo.titulo">
            <textarea v-if="conteudo.titulo" placeholder="Conteúdo" v-model="conteudo.texto" id="conteudo" class="materialize-textarea"></textarea>
            <input v-if="conteudo.titulo && conteudo.texto" type="text" placeholder="Link" v-model="conteudo.link"> 
            <input v-if="conteudo.titulo && conteudo.texto" type="text" placeholder="Url da imagem" v-model="conteudo.imagem"> 
            <label for="titulo">O que está acontecendo?</label>
            </grade>
            <p class="right-align">
            <button @click="addConteudo" v-if="conteudo.titulo && conteudo.texto" class="btn waves-effect waves-light" >Publicar</button>
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
        conteudo:{titulo:'',texto:'',link:'',imagem:''}
    };
  },
  components: {
    grade,
  },
  methods:{
    addConteudo(){
      this.$http.post(this.$urlAPI+'conteudo/adicionar',
      { titulo:this.conteudo.titulo,
       texto:this.conteudo.texto, 
       link:this.conteudo.link, 
       imagem:this.conteudo.imagem
      },
      {headers: { authorization: "Bearer " + this.$store.getters.getToken }} )
      .then(response => {
        if(response.data.status){
          console.log(response.data.conteudos);
          this.conteudo ={titulo:'',texto:'',link:'',imagem:''}
          document.location.reload(true);
        }
       else if (response.data.status == false && response.data.validacao) {
          console.log("Erro na validação");
          let erros = "";
          for (let erro of Object.values(response.data.erros)) {
            erros += erro + " ";
          }
          alert(erros);
        } 
      }).catch((e) => {
          alert(e);
      })
    }  
  }
}
</script>

<!-- Estilo da página -->
<style scoped>
</style>