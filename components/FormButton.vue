<template>
  <button :disabled="isDisabled" :class=" { 'disabled-button': isDisabled } ">
    <div v-if="!isLoading">{{ buttonText }}</div>
    <div v-else><loading-component></loading-component></div>
  </button>
</template>

<script>
import LoadingComponent from "~/components/Loading.vue";

export default {
  components: {
    LoadingComponent
  },
  props: {
    isLoading: {
      type: Boolean,
      default: false
    },
    isDisabled: {
      type: Boolean,
      default: true,
    },
    buttonText: {
      type: String,
      default: "GO!!!"
    }
  }
}
</script>

<style lang="css">
</style>
