<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdded="onAddQuote"></app-new-quote>
    <app-quote-grid
      :quotes="quotes"
      @quoteDeleted="onDeleteQuote"
    ></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">
          Info: click on a quote to delete it
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from './components/QuoteGrid.vue';
import NewQuote from './components/NewQuote.vue';
import Header from './components/Header.vue';

export default {
  data: function () {
    return {
      maxQuotes: 10,
      quotes: ['Just a quote to begin with something'],
    };
  },
  methods: {
    onAddQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert('Please delete some quotes first!');
      }
      this.quotes.push(quote);
    },
    onDeleteQuote(index) {
      this.quotes.splice(index, 1);
    },
  },
  components: {
    'app-quote-grid': QuoteGrid,
    'app-new-quote': NewQuote,
    'app-header': Header,
  },
};
</script>

<style></style>
