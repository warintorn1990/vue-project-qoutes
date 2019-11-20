<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
        <div class="row">
            <div class="col-sm-12 text-center">
                <div class="alert alert-info">Info: Click on a Quote to Delete it!</div>
            </div>
        </div>
    </div>
</template>

<script>
    import QuoteGrids from './conponents/QuoteGrids.vue';
    import NewQuote from './conponents/NewQuote.vue';
    import Header from './conponents/Header.vue';
    export default {
        data: function(){
            return{
                quotes: [
                    'อยากกินตีนไก่'
                ],
                maxQuotes: 10
            }
        },
        methods:{
            newQuote(quote){
                if(this.quotes.length >= this.maxQuotes){
                    return alert('Pleace delete Quotes first!!!');
                }
                this.quotes.push(quote);
            },
            deleteQuote(index){
                this.quotes.splice(index, 1);
            }
        },
        components:{
            appQuoteGrid: QuoteGrids,
            appNewQuote: NewQuote,
            appHeader: Header
        }
    }
</script>

<style>
</style>
