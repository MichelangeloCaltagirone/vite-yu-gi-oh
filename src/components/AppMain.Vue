<script>

import cardItem from './AppCard.vue';
import axios from 'axios';

    export default {
        data() {
            return {
                apiUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=120&offset=0',
                cardsList: [],
                awaitedCardsList: []
            }
        },
        components: {
            cardItem
        },
        methods: {
            getYugiohCardList(){
            axios.get(this.apiUrl).then(response => {
            console.dir(response.data.data);
            console.log(response.data.data[0].card_images[0].image_url, "mostro prova di ricerca");
            this.awaitedCardsList = response.data.data;
            console.log(this.awaitedCardsList[1].name, 'questa è la card list dinamica'); 
            console.log(this.response.data.data[10].archetype)     


            })
            }
        },
        created() {

            this.getYugiohCardList()
            setTimeout(() => {
            this.cardsList = this.awaitedCardsList;   
        }, 5000)
        }
}
</script>

<template>
    <main>
        <div class="containerCustom">

            <select name="" id=""></select>
            
            <section class="cardsList">

                <cardItem v-for="(card, index) in cardsList" :key="index"
                :picUrl="card.card_images[0].image_url"
                :name="card.name"
                :archetype="card.archetype"
                />

                <!-- <img :src="this.cardsList[index].card_images[0].image_url" :alt=this.cardsList[index].name> -->
            </section>

        </div>

    </main>
    
 
</template>

<style scoped>
main {
    background-color: burlywood;
}
.containerCustom {
    max-width: 1100px;
    margin: 0 auto;
}
.cardsList {
    display: flex;
    flex-wrap: wrap;
    padding: 2rem;
    background-color: white;
}

</style>