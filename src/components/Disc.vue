<template>
    <div class="disc">
        <img :src="info.poster" :alt="info.title">
        <h3>
            {{ info.title }}
        </h3>
        <h4>
            {{ info.author }}
        </h4>
        <h5>
            {{ info.year }}
        </h5>
    </div>
</template>

<script>
export default {
    name: 'Disc',
    props: {
        info: Object
    }
}
</script>

<style lang="scss" scoped>
.disc {
    text-align: center;
    width: calc((100% / 5) - 30px);
    background-color: #2e3a46;
    margin: 15px;
    padding: 25px;

    img {
        width: 100%;
    }

    h3 {
        color: white;
        text-transform: uppercase;
        margin: 10px 0;
    }

    h4,
    h5 {
        color: #62787f;
    }
}
</style>