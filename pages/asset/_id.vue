<template lang="html">
  <main class="gutter mtx">
    <h1 class="text-center mb">{{ retreivedItem.title }}</h1>
    <section class="text-center">
      <summary>
        {{ retreivedItem.description }}
      </summary>
      <figure class="mt">
        <img :src="retreivedItem.img" :alt="retreivedItem.title" />
      </figure>
    </section>


  </main>
</template>

<script>
export default {
  async asyncData({ $axios, params }){

    // lets get the asset from the NASA api
    const { data } = await $axios.get(`https://images-api.nasa.gov/search?nasa_id=${ params.id }`);
    const item = data.collection.items[0];

    // build a cleaner object
    return {
      retreivedItem: {
        description: item.data[0].description,
        img: item.links[0].href,
        title: item.data[0].title
      }
    }
  }
}
</script>

<style lang="css">
</style>
