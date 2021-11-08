<template>
    <img :src="apodImage" alt="">
</template>

<script>
export default {
    name: 'ApodImage',
    props: {
        apodImage: String, 
    }
}
</script>

<style scoped>
    img {
        width: 100%;
        height: auto;
        border-radius: 10px;
    }
</style>