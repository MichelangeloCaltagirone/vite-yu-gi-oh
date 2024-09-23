<script>
    export default {
        data() {
            return {
            }
        }
    }
</script>

<template>

    <div class="containerCustom">
        <img id="logoHeader" src="../assets/img/Yu-Gi-Ohlogo.png" alt="logo yugi">
        <h1>Yu-Gi-Oh API</h1>
    </div>

</template>


<style scoped>

#logoHeader {
    width: 100px;
    position: absolute;
    top: -35;
    left: -105px;
}
.containerCustom {
    max-width: 1100px;
    margin: 0 auto;
    padding: 2rem 0 2rem 10px;
    position: relative;

    h1 {
        display: inline;
        font-size: 30px
    }
}

</style>