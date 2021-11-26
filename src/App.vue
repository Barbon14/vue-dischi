<template>
  <div id="app">
    <header>

    </header>
    <main>
      <Discs/>
    </main>
  </div>
</template>

<script>
import Discs from "@/components/Discs.vue";

export default {
  name: 'App',
  components: {
    Discs
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
}
</style>
