<template>
  <main class="gutter mtx text-center">
    <h1 class="text-center mb">NASA Search</h1>
    <p class="mt mb">Search for cool images !</p>
    <button @click="handleForm">Get Searching !</button>
  </main>
</template>

<script>
export default {
  methods: {
    handleForm(){
      this.$router.push("/search");
    }
  }
}

</script>
