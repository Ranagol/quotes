<template>
    <div class="container">
        <app-new-quote @quoteAdded="newQuote"></app-new-quote><!--Here we are listening to our event  @quoteAdded-->
        <app-quote-grid :quotes="quotes"></app-quote-grid><!--WTF IS THIS :quotes="quotes"  -->
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
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
        },
        methods: {

            newQuote(quote){//since we added our whole qoute to the emitted event (this.$emit('quoteAdded', this.quote)) on the NewQuote.vue, now here on App.vue we have access to this this.quote..., and use it as an argument...

                this.quotes.push(quote);//and we are adding this received quote to our quotes array
            }
        }
    }
</script>

<style>
</style>
