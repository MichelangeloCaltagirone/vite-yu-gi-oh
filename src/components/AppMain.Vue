<script>

import cardItem from './AppCard.vue';
import axios from 'axios';

    export default {
        data() {
            return {
                apiUrl: 'https://db.ygoprodeck.com/api/v7/cardinfo.php?num=80&offset=0',
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
            console.log(this.response.data.data[10].archetype);
            console.log(this.awaitedCardsList.length)    


            })
            }
        },
        created() {

            this.getYugiohCardList()
            setTimeout(() => {
            this.cardsList = this.awaitedCardsList;   
        }, 5000)
        },
        computed: {
            answerLength() {
                return this.cardsList.length
            }
        }
}
</script>

<template>
    <main>
        <div class="containerCustom">

            <select name="" id="inputSearchField">
                <option value="Alien">Alien</option>
            </select>
            <div id="cardsSearched">Found {{ answerLength }} cards</div>
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
#cardsSearched {
    color: white;
    background-color: #212429;
    padding: 25px 20px;
    font-weight: bold;
}
#inputSearchField {
    margin: 1.5rem 0;
    padding: 15px 60px 15px 25px;
    font-size: 18px;
    font-weight: 400;
    border: none;
    border-radius: 15px;
}

</style>