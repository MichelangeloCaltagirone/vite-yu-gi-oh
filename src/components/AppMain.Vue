<script>
import AppCard from './AppCard.vue';
    export default {
        data() {
            return {
                cardsList: [

                ]
            }
        },
        components: {
            AppCard
        }
    }
</script>

<template>
    <div class="containerCustom">
        <h2>Sarò il main</h2>
    </div>
 
</template>

<style scoped>

.containerCustom {
    max-width: 1100px;
    margin: 0 auto;
}

</style>