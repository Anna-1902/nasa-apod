<template>
    <article>
        <p>
            {{apodDate}}
        </p>
    </article>
</template>

<script>
export default {
    name: 'ApodDate',
    props: {
        apodDate: String, 
    } 
}
</script>

<style scoped>
article {
    width: 50%;
}
p {
    margin-bottom: 1rem;
    margin-top: 0;
}
</style>