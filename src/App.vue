<template>
    <div class="container">
        <app-header :quoteCount="quotes.length" :maxQuotes="maxquotes"></app-header>
        <app-new-quote @quoteAdded="newQuote"></app-new-quote>
        <appQuoteGrid :quotes="quotes" @quoteDeleted="deleteQuote"></appQuoteGrid>
        <div class="row">
           <div class="col-sm-12 text-center">
               <div class="alert alert-info">Click on the quote to delete it!</div>
           </div>
        </div>
    </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid'
import NewQuote from './components/NewQuote'
import Header from './components/Header'

    export default {
        data(){
            return{
                quotes:["just a quotes to see"],
                maxquotes:10
            };
        },
        components: {
            appQuoteGrid: QuoteGrid,
            appNewQuote: NewQuote,
            appHeader: Header
        },
        methods:{
            newQuote(quote){
                if(this.quotes.length>=this.maxquotes){
                    return  alert("please delete some quotes");
                }
                this.quotes.push(quote);
            },
            deleteQuote(index){
                this.quotes.splice(index,1);
            }
        }
    }
</script>

<style>
</style>