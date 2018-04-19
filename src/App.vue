<template>
  <div class="container">
    <app-header :quoteCount="quotes.length" :maxQuotes="maxQuotes"></app-header>
    <app-new-quote @quoteAdd="newQuote"></app-new-quote>
    <app-quote-grid :quotes="quotes" @quoteDeleted="deleteQuote"></app-quote-grid>
    <div class="row">
      <div class="col-sm-12 text-center">
        <div class="alert alert-info">Info: Click on a Quote to delete it!</div>
      </div>
    </div>
  </div>
</template>

<script>
import QuoteGrid from "./components/QuoteGrid.vue";
import NewQuote from "./components/NewQuote.vue";
import Header from "./components/Header.vue";

export default {
  data() {
    return {
      quotes: [],
      maxQuotes: 10
    };
  },
  watch: {
    quotes: {
      handler(quotes) {
        this.save(quotes);
      },
      deep: true
    }
  },
  methods: {
    newQuote(quote) {
      if (this.quotes.length >= this.maxQuotes) {
        return alert("Please delete Quote!");
      }
      this.quotes.push(quote);
    },
    deleteQuote(index) {
      this.quotes.splice(index, 1);
    },
    fetch() {
      let quotes = JSON.parse(localStorage.getItem("quotes"));
      this.quotes = quotes || [
        "不要害怕，要勇敢的向前走。",
        "Go confidently in the direction of your dreams. Live the life you've imagined. As you simplify your life, the laws of the universe will be simpler."
      ];
    },
    save(quotes) {
      localStorage.setItem("quotes", JSON.stringify(quotes));
    }
  },
  components: {
    appQuoteGrid: QuoteGrid,
    appNewQuote: NewQuote,
    appHeader: Header
  },
  mounted() {
    this.fetch();
  }
};
</script>

<style lang="scss">

</style>
