<template id="app">
  <NavigationBar/>
  <AppFooter/>
</template>

<script>
import NavigationBar from './components/NavigationBar.vue'
import AppFooter from "./components/Footer";
export default {
  name: 'App',
  components: {
     NavigationBar, AppFooter
  }
}
</script>

<style>

</style>
