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
        <div>{{ name }}</div>
        <div>{{ archetype }}</div>
    </article>

</template>

<style scoped>
article {
    display: inline;
    flex-basis: calc(100% / 5);
    img {
        height: 250px;
    }
}
</style>