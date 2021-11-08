<template>
  <main>
    <div class="titles">
      <h1>NASA Astonomy Picture of the Day</h1>
      <ApodTitle v-bind:apodTitle="apod.title" />
      <ApodDate v-bind:apodDate="apod.date" />
      <ApodCopyright v-if="apod.copyright" v-bind:apodCopyright="apod.copyright"/>
    </div>

      <div v-if="show" class="picture">
        <ApodImage v-if="apod.media_type == 'image'" v-bind:apodImage="apod.hdurl"
        />
      </div>
      <div v-else class="picture">
        <ApodImage v-if="apod.media_type == 'image'" v-bind:apodImage="apod.url"
        />
      </div>

    <div class="explanation">
      <button v-if="show == false" @click="show = !show">See HD version</button>

      <button v-else @click="show = !show" id="hide">Go back to NOT HD</button>

      <ApodExplanation v-bind:apodExplanation="apod.explanation" />
    </div>
  </main>
</template>

<script>
import axios from "axios";
import ApodTitle from "./components/ApodTitle.vue";
import ApodDate from "./components/ApodDate.vue";
import ApodImage from "./components/ApodImage.vue";
import ApodExplanation from "./components/ApodExplanation.vue";
import ApodCopyright from "./components/ApodCopyright.vue";

export default {
  name: "App",
  components: {
    ApodTitle,
    ApodDate,
    ApodImage,
    ApodExplanation,
    ApodCopyright,
  },
  data() {
    return {
      apod: {
        title: "",
      },
      show: false,
      token: process.env.VUE_APP_TOKEN,
    };
  },
  created() {
    axios
      .get("https://api.nasa.gov/planetary/apod?api_key=" + this.token)
      .then((response) => {
        this.apod = response.data;
      });
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
}
main {
  margin: 1rem 5rem;

  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  flex-wrap: wrap;
}
h1 {
  width: 100%;
  margin-bottom: 2rem;
  padding-bottom: 1rem;
  border-bottom: 3px solid peachpuff;
}

.titles {
  width: 100%;
}

.picture {
  width: 50%;
  margin-right: 2rem;
}

.explanation {
  width: 40%;

  display: flex;
  flex-direction: column;
}
button {
    padding: .5rem;
    margin-top: 0;
    margin-bottom: 2rem;

    width: fit-content;
    height: fit-content;

    background-color: white;
    border: 3px solid peachpuff;
    border-radius: 10px;
    box-shadow: 14px 6px 35px 4px rgba(140,140,140,0.35);
}
#hide{
    padding: .5rem;
    margin-top: 0;
    margin-bottom: 2rem;
    background-color: peachpuff;
    border: 3px solid rgba(140,140,140,0.35);
    border-radius: 10px;
    box-shadow: 14px 6px 35px 4px rgba(140,140,140,0.35);

}
</style>
