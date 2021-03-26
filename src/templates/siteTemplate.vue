<template>
  <span>
    <header>
      <navbar url="/" cor="teal darken-2" logo="Social">
          <li ><router-link to="/">Home</router-link></li>
          <li v-if="usuario == false"><router-link to="/login">Entrar</router-link></li>
          <li v-if="usuario"><router-link to="/perfil">{{usuario.name}}</router-link></li>
          <li v-if="usuario"><a v-on:click="sair()" to="/login">Sair</a></li>
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
               
              </cartaomenu>  
          </grade>
          <grade tamanho="8">
           <slot name="principal"/>
          </grade>
        </div>
      </div>
    </main>
    <rodape style="position:absolut;bottom:0;widht:100%" cor="teal darken-2" logo="Social" descricao="SPA utilizando Vue.js e Laravel" ano="2021">
      <li ><router-link to="/">Home</router-link></li>
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
  data(){
    return{
      usuario: false
    }
  },
  created(){
    let usuarioAux = this.$store.getters.getUsuario;
    if(usuarioAux){
       this.usuario = this.$store.getters.getUsuario;
    }else{
      this.$router.push('/login');
    }
  },
  methods:{
    sair(){
      this.$store.commit('setUsuario',null);
      sessionStorage.clear();
      this.usuario = false;
      this.$router.push('/login');
    }
  }
};
</script>

<style>
body{
  background-color: rgb(255, 255, 255);
}
</style>
