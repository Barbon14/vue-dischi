<template>
    <section id="discs-container">
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
            apiDiscs : [],
            apiUrl : 'https://flynn.boolean.careers/exercises/api/array/music',
            allGenres : []
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
                return item.genre === this.selectedGenre;
            });
        }
    },
    methods: {
        getApiDiscs () {
            axios
            .get(this.apiUrl)
            .then((result) => {
                this.apiDiscs = result.data.response;
                this.apiDiscs.forEach((disc) => {
                    if (!this.allGenres.includes(disc.genre)) {
                        this.allGenres.push(disc.genre);
                    }
                    console.log(this.allGenres);
                });
                this.$emit('genresList', this.allGenres);
            })
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