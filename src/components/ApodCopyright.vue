<template>
    <article>
        <p>
            By: {{apodCopyright}}
        </p>
    </article>
</template>

<script>
export default {
    name: 'ApodCopyright',
    props: {
        apodCopyright: String, 
    } 
}
</script>

<style scoped>
article {
    width: 50%;
}
</style>