<template>
    <div>
        <label>
            Scegli un genere
        </label>
        <select v-model="genreSelect" @change="$emit('genre', genreSelect)">
            <option value=""></option>
            <option value="rock">Rock</option>
            <option value="pop">Pop</option>
            <option value="jazz">Jazz</option>
            <option value="metal">Metal</option>
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
    }
}
</script>

<style lang="scss" scoped>
label {
    color: white;
}
</style>