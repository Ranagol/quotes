<template>
    <div class="container">
        <app-new-quote @quoteAdded="newQuote"></app-new-quote><!--Here we are listening to our event  @quoteAdded-->
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid><!--WTF IS THIS :quotes="quotes"  -->
        <div class="row">
            <div class="text-center">
                <div class="alert alert-info">Info: click on a quote to delete it</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrid from './components/QuoteGrid.vue';
    import NewQuote from './components/NewQuote.vue';
    export default {
        data(){
            return {
                quotes: [
                    'Just a quote to see something',
                ],
                maxQuotes: 10,
            }
        },
        methods: {

            newQuote(quote){//since we added our whole qoute to the emitted event (this.$emit('quoteAdded', this.quote)) on the NewQuote.vue, now here on App.vue we have access to this this.quote..., and use it as an argument...

                this.quotes.push(quote);//and we are adding this received quote to our quotes array
            },

            deleteQuote(index){//the index was sent here from where the @quoteDeleted emit happened
                this.quotes.splice(index, 1);//delete this index number, and delete only 1 element
            }


        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
        },
        
    }
</script>

<style>
</style>
