<template>
  <div id="app">
    <Nav />
    <Me />
  </div>
</template>

<script>
import Me from './components/Me.vue'
import Nav from './components/Nav.vue'

export default {
  name: 'app',
  components: {
    Me,
    Nav
  }
}
</script>

<style>
* {
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
</style>
