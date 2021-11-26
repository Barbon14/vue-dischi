<template>
  <section id="discs-container">
    <Disc
        v-for="disc, i in apiDiscs" :key="i"
        :info="disc"
    />
  </section>
</template>

<script>
import Disc from "@/components/Disc.vue";

import axios from "axios";

export default {
    name: 'Discs',
    components: {
        Disc
    },
    data () {
        return {
            apiDiscs : [],
            apiUrl : 'https://flynn.boolean.careers/exercises/api/array/music'
        }
    },
    created () {
        this.getApiDiscs();
    },
    methods: {
        getApiDiscs () {
            axios
            .get(this.apiUrl)
            .then((result) => {
                this.apiDiscs = result.data.response
            })
        }
    }
}
</script>

<style lang="scss" scoped>
#discs-container {
    width: 70%;
    margin: 0px auto;
    display: flex;
    flex-wrap: wrap;
}
</style>