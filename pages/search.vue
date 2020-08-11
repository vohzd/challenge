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
  </main>
</template>


<script>

export default {

  methods: {
    handleForm(){
      console.log("clicked");
      this.$router.push("/asset/something");
    }
  }

}

</script>
