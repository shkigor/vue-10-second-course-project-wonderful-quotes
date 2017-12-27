<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
  import Header from './components/Header';
  import QuoteGrid from './components/QuoteGrid';
  import NewQuote from './components/NewQuote';

  export default {
    data: function () {
      return {
        quotes: [
                'Just a Quote to see something'
        ],
        maxQuotes: 10
      }
    },
    methods: {
      newQuote(quote) {
        if (this.quotes.length >= this.maxQuotes) {
          return alert('Please delete Quotes first!');
        }
        this.quotes.push(quote);
      },
      deleteQuote(index) {
        // let index = this.quotes.indexOf(quote);
        if (index > -1) {
          this.quotes.splice(index, 1);
        }
      }
    },
    watch: {
      quotes: function (value) {
        if (value.length >= this.maxQuotes) {
          console.log('Quotes full!');
        }
      }
    },
    components: {
      appHeader: Header,
      appQuoteGrid: QuoteGrid,
      appNewQuote: NewQuote
    }

  }
</script>

<style>
</style>
