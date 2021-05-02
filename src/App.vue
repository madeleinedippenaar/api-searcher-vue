<template>
  <div id="app">
    <Search />
  </div>
</template>

<script>
import Search from './components/Search'

export default {
  name: 'App',
  components: {
    // eslint-disable-next-line vue/no-unused-components
    Search
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
body {
  background-color: #2E5339;
  color: #FFCCC9;
  }

</style>
