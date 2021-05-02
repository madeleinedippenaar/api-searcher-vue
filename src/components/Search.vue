<template>
  <div class="api-app">
    <div id="intro=wrapper">
      <div id="intro-content">
        <div><h1>Welcome!</h1></div>
        <h3>This is my first app built with Vue, using api.publicapis.org </h3>
        <h4>Enjoy! :)</h4>
      </div>
    </div>
    <div class="search">
      <input v-model="term" type="search"> <button @click="search"> Search </button>
    </div>
    <div v-if="results">
      <result v-for="result in results" :key="result.Link" :link="result.Link" :api="result.API" :desc="result.Description" />
    </div>
    <div v-if="!results" id="init-result-message">
      Search results appear here!
    </div>
  </div>
</template>

<script>
import Result from './Result.vue';
export default {
  components: { Result },
  name: 'Search',
  data() {
    return {
      term: '',
      results: null
    }
},
methods: {
  search() {
    if(this.term.trim() === '') return;
    console.log('Search for ' + this.term);
    fetch(`https://api.publicapis.org/entries?title=${encodeURIComponent(this.term)}`)
    .then(res => res.json())
    .then(res => {
      console.log('results', res);
        this.results = res.entries;
      });
    }
  }
}
</script>

// <!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
#intro-content {
  text-align: center;
  }
#init-result-message {
  display: flex;
  justify-content: center;
  }
.search {
  display: flex;
  justify-content: center;
  }

</style>