<template>
  <div class="row">
    <app-quote v-for="quote in quotes">{{ quote }}</app-quote>
  </div>
</template>

<script>
import Quote from './Quote.vue';
export default {
  props: ['quotes'],//in props we can receive properties from the parent component. quotes property is defined in App.vue/data.
  components: {
    appQuote: Quote,
  }

}
</script>

<style>

</style>