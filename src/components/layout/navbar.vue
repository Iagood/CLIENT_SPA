<template>
    <nav class="teal darken-2">
      <div class="nav-wrapper container">
        <a :href="url || '#/'" class="brand-logo">{{logo || 'Site'}}</a>
        <ul id="nav-mobile" class="right hide-on-med-and-down">
            <slot />
        </ul>
      </div>
    </nav>
</template>

<script>
export default {
  name: 'Navbar',
  props:['logo','url','cor'],
  data () {
    return {
     
    }
  }
}
</script>

<!-- Estilo da página -->
<style scoped>

</style>