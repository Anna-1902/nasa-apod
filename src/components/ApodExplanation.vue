<template>
    <article>
        <button v-if="show ==false" @click="show = !show">
            See explanation
        </button>

        <button v-else @click ="show = !show" id="hide">
            Hide explanation
        </button>
        
        <div v-if="show">
            <p>
                {{apodExplanation}}
            </p>
        </div>
    </article>
</template>

<script>
export default {
    name: 'ApodExplanation', 
    props: {
        apodExplanation: String, 
    },
    data () {
        return {
            show: false,
        }
    }
}
</script>

<style scoped>
article {
    width: 100%;
}

p {
    line-height: 2rem;
}

button {
    padding: .5rem;
    margin-top: 0;
    margin-bottom: .5rem;
    background-color: none;
    border: 3px solid peachpuff;
    border-radius: 10px;
    box-shadow: 14px 6px 35px 4px rgba(140,140,140,0.35);
}

#hide{
    padding: .5rem;
    margin-top: 0;
    margin-bottom: .5rem;
    background-color: peachpuff;
    border: 3px solid rgba(140,140,140,0.35);
    border-radius: 10px;
    box-shadow: 14px 6px 35px 4px rgba(140,140,140,0.35);

}

</style>