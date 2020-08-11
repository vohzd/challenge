<template>
  <main class="gutter mtx">
    <h1 class="text-center mb">NASA Search</h1>
    <div class="flex-wrapper">
      <input class="c75" placeholder="Search anything (e.g Rover)" @keyup.enter="handleForm">
      <button class="c25" @click="handleForm">GO!!!</button>
    </div>
  </main>
</template>

<script>

export default {

  methods: {
    handleForm(){
      console.log("clicked");
      this.$router.push("/search");
    }
  }

}

</script>
