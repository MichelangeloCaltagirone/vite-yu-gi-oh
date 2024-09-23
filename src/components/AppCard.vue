<script>
 export default {
        data() {
            return {

            }
        },
        props: {
            picUrl: {
                type: String,
                required: true
            },
            archetype: {
                type: String,
                required: false
            },
            name: {
                type: String,
                required: true
            }
        },
        methods: { 
            getImageUrl(picPath) {
                return new URL(`../assets/img/${picPath}`, import.meta.url).href
            }
        }
    
    }
</script>

<template>

    <article>
        <img :src="picUrl" :alt="name">
        <div id="name">{{ name }}</div>
        <div id="archetype">{{ archetype }}</div>
    </article>

</template>

<style scoped>
article {
    background-color: burlywood;
    margin: 0 auto 1.5rem auto;
    
    text-align: center;
    height: 480px;
    #name {
        color: white;
        font-weight: bold;
        margin: 20px 0;
        max-width: 240px;
    }
    img {
        height: 350px;
    }
    
}
</style>