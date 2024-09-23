<script>

import cardItem from './AppCard.vue';
import AppLoader from './AppLoader.vue';
import axios from 'axios';

    export default {
        data() {
            return {
                apiUrl: "https://db.ygoprodeck.com/api/v7/cardinfo.php",
                cardsList: [],
                awaitedCardsList: [],
                loading: true
            }
        },
        components: {
            cardItem,
            AppLoader
        },
        methods: {
            getYugiohCardList(){
            axios.get(this.apiUrl, {
                params: {
                    num: 80,
                    offset: 0
                }
            })            
            .then(response => {
           
            this.awaitedCardsList = response.data.data})}
        },
        created() {

            this.getYugiohCardList()
            setTimeout(() => {
            this.cardsList = this.awaitedCardsList;
            this.loading = false 
        }, 4000)
        },
        computed: {
            answerLength() {
                return this.cardsList.length
            }
        }
}
</script>

<template>
    <AppLoader v-if="loading" />
    <main v-else>

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