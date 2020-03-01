<template>
  <div class="row">
    <app-quote v-for="(quote, index) in quotes" @click.native="deleteQuote(index)">{{ quote }}</app-quote><!--Here we want our our selected quote to respond to our mouse click. The 'native' event modifier tells Vue to react to the click. Otherwise this reaction to the click would not work. Vue will register a click on Quote.vue, around the slot. Native means that even thouhg the click happened in html DOM, it will be treated like the click happened in the app-quote. In sum: use .native when you need the 'raw' event from DOM. 
    With this, we will be able to execute the deleteCode method.-->
  </div>
</template>

<script>
import Quote from './Quote.vue';
export default {
  props: ['quotes'],//in props we can receive properties from the parent component. quotes property is defined in App.vue/data.
  components: {
    appQuote: Quote,
  },
  methods: {
    deleteQuote(index){//how to determine which quote to delete? We need the index of the right quote. So we do this: v-for="(quote, index). This way we can get our index. this index is passed as argument into the deleteQuote().

      this.$emit('quoteDeleted', index);

    }
  }

}
</script>

<style>

</style>