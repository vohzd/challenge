<template>
  <main class="gutter">
    <h1 class="text-center mb">NASA Search</h1>
    <div class="flex-wrapper">
      <input class="c75" placeholder="Search anything (e.g Rover)" @keyup.enter="handleForm">
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

      <div class="flex-grid">
        <div v-for="i in 32" class="flex-grid-item mock-asset">
          {{ i }}
        </div>
      </div>


    </section>


  </main>
</template>


<script>
  export default {
    methods: {
      handleForm(){
        console.log("searched for something....");
      },
      handleAsset(){
        this.$router.push("/asset/something");
      }
    }
  }
</script>

<style>

  .mock-asset {
    min-height: 64px;
    min-width: 64px;
    background: rgba(0,0,0,0.2);
  }

</style>
