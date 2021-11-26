<template>
  <section id="discs-container">
    <Disc/>
  </section>
</template>

<script>
import Disc from "@/components/Disc.vue";

export default {
  name: 'Discs',
  components: {
    Disc
  }
}
</script>

<style lang="scss" scoped>
#discs-container {
    width: 80%;
    margin: 0px auto;
}
</style>