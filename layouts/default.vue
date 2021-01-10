<template>
  <div>
    <NavBar />
    <hr class="divider"/>
    <Nuxt />
  </div>
</template>

<script>
import NavBar from '~/components/NavBar.vue'

export default {
  components: { NavBar }
}
</script>

<style>
html {
  font-family: sans-serif;
  font: 'Noto Sans';
  margin: 0;
  padding: 0;
}
.divider {
  margin: 0;
}
</style>
