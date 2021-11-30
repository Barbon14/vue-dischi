<template>
    <div>
        <label>
            Scegli un genere
        </label>
        <select v-model="genreSelect" @change="$emit('genre', genreSelect)">
            <option value="">Tutti</option>
            <option v-for="(genre, i) in list" :key="i" :value="genre">
                {{ genre }}
            </option>
        </select>
    </div>
</template>

<script>
export default {
    name: 'FilterGenre',
    data() {
        return {
            genreSelect: "",
        }
    },
    props: {
        list : Array
    } 
}
</script>

<style lang="scss" scoped>
label {
    color: white;
}
</style>