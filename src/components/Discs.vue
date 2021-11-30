<template>
    <section id="discs-container">
        <!-- stampo i dischi -->
        <Disc
            v-for="(disc, i) in filteredApiDiscs" :key="i"
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
        Disc,
    },

    props: {
        selectedGenre : String
    },
    data () {
        return {
            // url del API
            apiUrl : 'https://flynn.boolean.careers/exercises/api/array/music', 
            // array dischi 
            apiDiscs : [],
            // array generi
            allGenres : []
        }
    },
    created () {
        // richiamo metodo per chiamata axios
        this.getApiDiscs();
    },
    computed: {
        // filtro i dischi per genere
        filteredApiDiscs() {
            if ( this.selectedGenre === "") {
                return this.apiDiscs;
            }

            return this.apiDiscs.filter((item) => {
                return item.genre === this.selectedGenre;
            });
        }
    },
    methods: {
        // uso un metodo per fare la chiamata axios
        getApiDiscs () {
            axios
            .get(this.apiUrl)
            .then((result) => {
                // genero la lista dei dischi
                this.apiDiscs = result.data.response;
                // genero la lista dei generi senza doppioni
                this.apiDiscs.forEach((disc) => {
                    if (!this.allGenres.includes(disc.genre)) {
                        this.allGenres.push(disc.genre);
                    }
                });
                // emetto la lista generi
                this.$emit('genresList', this.allGenres);
            })
            // stampo in console eventuale errore chiamata axios
            .catch ((err) => {
                console.log(err);
            });
        },
    }
}
</script>

<style lang="scss" scoped>

#discs-container {
    display: flex;
    flex-wrap: wrap;
}

</style>