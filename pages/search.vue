<template>
  <main class="gutter">
    <h1 class="text-center mb">NASA Search</h1>
    <div class="flex-wrapper">
      <input class="c75" placeholder="Search anything (e.g Rover)" @keyup.enter="handleForm" v-model="searchQuery">
      <button class="c25" @click="handleForm">GO!!!</button>
    </div>
    <div class="row">
      <span class="flex-wrapper text-center">
        <div class="c50">
          <input id="images-checkbox" type="checkbox">
          <label for="images-checkbox">Images</label>
        </div>
        <div class="c50">
          <input id="audio-checkbox" type="checkbox">
          <label for="audio-checkbox">Audio</label>
        </div>
      </span>
    </div>


    <section class="output">
      <!-- this will become its own component soon enough -->

      <div class="flex-grid mtx">
        <div v-for="result in results" class="flex-grid-item">
          <nuxt-link :to="`/asset/${result.data[0].nasa_id}`">
            <span :style='generateBackgroundImage(result.links[0].href)'></span>
          </nuxt-link>
        </div>
      </div>


    </section>


  </main>
</template>


<script>
  export default {
    data () {
      return {
        searchQuery: null,
        results: []
      }
    },
    methods: {
      handleForm(){
        if (!this.searchQuery) return;
        this.queryApi();
      },
      handleAsset(){
        this.$router.push("/asset/something");
      },
      generateBackgroundImage(url){
        // this is a hack for now until we find a suitable thumbnail (and can place in a proper <img />) tag
        return `background-image: url(${url}); background-size: cover; display: inline-block; min-width: 128px; min-height: 128px; top:0; left: 0; z-index: 1; border-radius: 3px;`;
      },
      async queryApi(){
        console.log("querying...")
        try {
          const { data } = await this.$axios.get(`https://images-api.nasa.gov/search?&media_type=image&q=${ this.searchQuery }`);
          this.results = data.collection.items;
          console.log(this.results)
        }
        catch (e){
          console.log(e)
        }

      }
    }
  }
</script>

<style>



</style>
