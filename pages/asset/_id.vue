<template lang="html">
  <main class="gutter mtx">

    <h1 class="text-center mb">{{ retreivedItem.title }}</h1>
    <section class="text-center">
      <summary>
        {{ retreivedItem.description }}
      </summary>

      <figure class="mt">
        <img v-if="retreivedItem.type === 'image'" :src="retreivedItem.mediaUrl" :alt="retreivedItem.title" />
        <audio v-if="retreivedItem.type === 'audio'" controls>
          <source :src="retreivedItem.mediaUrl" type="audio/mpeg" />
        </audio>
      </figure>-
    </section>

  </main>
</template>

<script>
export default {
  async asyncData({ $axios, params }){

    // lets get the asset from the NASA api
    const { data } = await $axios.get(`https://images-api.nasa.gov/search?nasa_id=${ params.id }`);

    // this is janky, but works for now... it will need refactoring to allow for more broader api json responses.
    const item = data.collection.items[0];
    const type = item.data[0].media_type;

    let mediaUrl;

    // if its an audio file, you'll get a .json file with some urls to files in
    if (type === "audio"){
      const mediaReq = await $axios.get("https://images-assets.nasa.gov/audio/Launch-sound_atlasLiftoff/collection.json");
      // find the .mp3
      const mp3 = mediaReq.data.filter((arrItem) => {
        return arrItem.indexOf(".mp3") > -1;
      })
      mediaUrl = mp3[0];
    }
    else if (type === "image"){
      mediaUrl = item.links[0].href;
    }

    // build a cleaner object
    return {
      retreivedItem: {
        description: item.data[0].description,
        mediaUrl,
        type,
        title: item.data[0].title
      }
    }
  }
}
</script>

<style lang="css">
</style>
