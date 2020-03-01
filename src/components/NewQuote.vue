<template>
  <div class="row">
    <form><!--THE INPUT FORM- -->
      <div class="form-group">
        <label for="textarea">Quote</label>
        <textarea id="textarea" class="form-control" rows="3" v-model="quote"></textarea>
      </div>
      <div class="form-group">
        <button class="btn btn-primary" @click.prevent="createNew">Add quote</button><!--prevent prevents the default behaviour of the button, because we don't want to send, submit with this button, we only want to execute our createNew method  -->
      </div>
    </form>
    
  </div>
</template>

<script>

export default {
  data(){
    return{
      quote: '',//this is two way binded to the textarea
    }
  },
  methods:{
    createNew(){
      this.$emit('quoteAdded', this.quote);//here we are sending the newly created quote... Here we are emitting.
      this.quote = '';//and after that, we are resetting it to be empty again
    }
  }
}
</script>

<style>

</style>