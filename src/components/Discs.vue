<template>
    <div class="container">
        <FilterGenre @genre="genreFilter"/>
        <section id="discs-container">
            <Disc
                v-for="disc, i in filteredApiDiscs" :key="i"
                :info="disc"
            />
        </section>
    </div>
</template>

<script>
import Disc from "@/components/Disc.vue";
import FilterGenre from "@/components/FilterGenre.vue";

import axios from "axios";

export default {
    name: 'Discs',
    components: {
        Disc,
        FilterGenre
    },
    data () {
        return {
            apiDiscs : [],
            apiUrl : 'https://flynn.boolean.careers/exercises/api/array/music',
            selectedGenre: ""
        }
    },
    created () {
        this.getApiDiscs();
    },
    computed: {
        filteredApiDiscs() {
            if ( this.selectedGenre === "") {
                return this.apiDiscs;
            } 

            return this.apiDiscs.filter((item) => {
                return item.genre.toLowerCase() === this.selectedGenre;
            });
        }
    },
    methods: {
        getApiDiscs () {
            axios
            .get(this.apiUrl)
            .then((result) => {
                this.apiDiscs = result.data.response
            })
        },
        genreFilter(genre) {
            this.selectedGenre = genre;
            console.log(this.selectedGenre);
        }
    }
}
</script>

<style lang="scss" scoped>
.container {
    width: 70%;
    margin: 0px auto;

    #discs-container {
        display: flex;
        flex-wrap: wrap;
    }
}
</style>