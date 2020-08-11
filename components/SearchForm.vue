<template lang="html">
  <div class="">
    <div class="flex-wrapper">
      <input class="c75" placeholder="Search anything (e.g Rover)" @keyup.enter="handleForm" v-model="searchQuery">
      <form-button @click.native="handleSearch" :is-loading="isLoading" :is-disabled="isDisabled" :button-text="buttonText"></form-button>
    </div>
    <div class="row">
      <small class="text-center mt mb row">Media Type (optional)</small>
      <span class="flex-wrapper text-center">
        <div class="flex-item c50">
          <input id="images-checkbox" value="image" type="checkbox" v-model="selectedMediaTypes">
          <label for="images-checkbox">Images</label>
        </div>
        <div class="flex-item c50">
          <input id="audio-checkbox" value="audio" type="checkbox" v-model="selectedMediaTypes">
          <label for="audio-checkbox">Audio</label>
        </div>
      </span>
    </div>
    <section class="output text-center">
      <div class="flex-grid mtx" v-if="results.length > 0">
        <div v-for="result in results" class="flex-grid-item" >
          <nuxt-link :to="`/asset/${result.data[0].nasa_id}`">
            <span v-if="result.data[0].media_type === 'image'">
              <span :style='generateBackgroundImage(result.links[0].href)'></span>
            </span>
            <span v-if="result.data[0].media_type === 'audio'">
              AUDIO
              {{ result.data[0].title }}
            </span>
          </nuxt-link>
        </div>
      </div>
      <small v-else class="mtx row">
        No results...
      </small>
    </section>
  </div>
</template>

<script>

import FormButton from "~/components/FormButton.vue";

export default {
  components: {
    FormButton
  },
  data (){
    return {
      buttonText: "GO!!!!",
      isLoading: false,
      isDisabled: true,
      searchQuery: null,
      selectedMediaTypes: [ "image" ],
      results: []
    }
  },
  methods: {
    async handleSearch () {
      this.isLoading = true;
      await this.queryApi();
      this.isLoading = false;
      this.buttonText = "Retreived!";
    },
    generateBackgroundImage(url){
      // this is a hack for now until we find a suitable thumbnail (and can place in a proper <img />) tag
      return `background-image: url(${url}); background-size: cover; display: inline-block; min-width: 128px; min-height: 128px; top:0; left: 0; z-index: 1; border-radius: 3px;`;
    },
    async queryApi(){
      const types = this.selectedMediaTypes.join(",");

      // this could probably do with a refactor...
      const q = types ? `?q=${ this.searchQuery }&media_type=${ types }` : `?q=${ this.searchQuery }`;

      // go and get the items !
      try {
        const { data } = await this.$axios.get(`https://images-api.nasa.gov/search${q}`);
        this.results = data.collection.items;
      }
      catch (e){
        // do some fancy error logging here...
        console.log(e)
      }
    }
  },
  watch: {
    searchQuery(){
      !this.searchQuery ? this.isDisabled = true : this.isDisabled = false;
    }
  },
}
</script>
