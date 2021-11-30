<template>
  <div id="app">
    <header>
      <!-- logo -->
    </header>
    <main>
      <div class="container">
        <FilterGenre :list="genresList" @genre="genreFilter"/>
        <Discs :selectedGenre="genreSearch" @genresList="getGenersList"/>
      </div>
    </main>
  </div>
</template>

<script>
import Discs from "@/components/Discs.vue";
import FilterGenre from "@/components/FilterGenre.vue";

export default {
  name: 'App',
  components: {
    Discs,
    FilterGenre
  },
  data() {
    return {
      genresList: [],
      genreSearch: ""
    }
  },
  methods: {
    genreFilter(genre) {
      this.genreSearch = genre;
    },
    getGenersList(allGenres) {
      this.genresList = allGenres;
    }
  }
}
</script>

<style lang="scss">
* {
  box-sizing: border-box;
  padding: 0;
  margin: 0;
}

body {
  font-family: sans-serif;
}

header {
  background-color: #2e3a46;
  height: 80px;
  width: 100vw;
}

main {
  background-color: #1e2d3b;
  height: calc(100vh - 80px);
  width: 100vw;
  padding-top: 50px;
  overflow: auto;

  .container{
    width: 70%;
    margin: 0 auto;
  }
}
</style>
