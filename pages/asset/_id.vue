<template lang="html">
  <main class="gutter mtx">
    <h1 class="text-center mb">{{ assetTitle }}</h1>
  </main>
</template>

<script>
export default {

  async asyncData({ store, params }){

    /*

      Runs server-side, equivalent to reacts get getStaticProps/getServerSideProps

      this is mocked... for now

    */
    return {
      assetTitle: params.id
    }
  }

}
</script>

<style lang="css">
</style>
