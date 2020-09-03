<template>
  <div id="app">
    <FirstComponent />
  </div>
</template>

<script>
import FirstComponent from './components/FirstComponent.vue'

export default {
  name: 'App',
  components: {
    FirstComponent
  }
}
</script>

<style>
@import url('./assets/styles/main.scss');
</style>
