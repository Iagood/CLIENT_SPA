<template>
  <loginTemplate>
    <h2>Login</h2>
    <span slot="menuesquerdo">
        <ul>
            <li>Item 1 </li>
            <li>Item 2 </li>
        </ul>    
    </span>    
    <span slot="principal">
      <input type="text" placeholder="E-mail" value="" />
      <input type="password" placeholder="Senha" value="" />
      <button type="button" class="btn">Entrar</button>
    </span>
  </loginTemplate>



</template>

<script>
import publicarConteudo from "@/components/social/publicarConteudo";
import cartaoConteudo from "@/components/social/cartaoConteudo";
import cartaoDetalhe from "@/components/social/cartaoDetalhe";
import grade from "@/components/layout/grade";
import loginTemplate from "@/templates/loginTemplate";

export default {
  name: "Login",
  data() {
    return {};
  },
  components: {
    cartaoConteudo,
    cartaoDetalhe,
    grade,
    publicarConteudo,
    loginTemplate,
  },
};
</script>

<!-- Estilo da página -->
<style scoped>
</style>
