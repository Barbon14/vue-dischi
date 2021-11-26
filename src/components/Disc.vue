<template>
    <div class="disc">
        <img src="https://www.ibs.it/images/0194398243825_0_0_200_75.jpg" alt="">
        <h3>
            titolo disco
        </h3>
        <h4>
            artista
        </h4>
        <h5>
            1999
        </h5>
    </div>
</template>

<script>
export default {
  name: 'Disc'
}
</script>

<style lang="scss" scoped>
.disc {
    text-align: center;
    width: calc((100% / 5) - 20px);
    background-color: #2e3a46;
    margin: 0 10px;
    padding: 10px 0;

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