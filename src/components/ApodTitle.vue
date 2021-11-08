<template>
    <article>
        <h2>
            {{apodTitle}}
        </h2>
    </article>
</template>

<script>
export default {
    name: 'ApodTitle',
    props: {
        apodTitle: String, 
    } 
}
</script>

<style scoped>
article {
    width: 50%;
}
h2 {
    margin-bottom: .5rem;
}
</style>