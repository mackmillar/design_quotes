<template lang="html">

  <div id="app">
    
    <quote-header logo="Design Quotes" :date= "quotes[randomise]['date'] | formatDate"></quote-header>

    <transition name="slide-fade" mode="out-in">
    <h1 :key="quotes[randomise]['content']['rendered']" v-html="quotes[randomise]['content']['rendered'].replace(/<\/?[^>]+>/gi,'')">"}}</h1>
    </transition>

    <quote-footer :author="quotes[randomise]['title']['rendered']"></quote-footer>

  </div>
</template>

<script charset="utf-8">
import { eventBus } from "@/main.js";
import QuoteHeader from './components/QuoteHeader.vue';
import QuoteFooter from './components/QuoteFooter.vue';

export default {
  name: 'App',
  data() {
    return {
      quotes: [],
      randomise: 0
    };
  },
  components: {
    "quote-header": QuoteHeader,
    "quote-footer": QuoteFooter
    
  },
  computed: {
    random: function() {
      return Math.floor(Math.random() * 11);  
    },
  },
  mounted(){
      this.fetchQuotes();
  
      eventBus.$on("new-quote", () => {
        this.randomise = Math.floor(Math.random() * 11);
        randomColor();
      });
      
    },
  methods: {
      fetchQuotes: function(){
        fetch("https://quotesondesign.com/wp-json/wp/v2/posts/?orderby=rand")
          .then(response => response.json())
          .then(data => this.quotes = data);
      },
},

}

</script>



<style>


#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #181818;
  margin-top: 40px;
  margin-bottom: 40px;
  margin-left: 40px;
  margin-right: 40px;
  height: 100vh;
}

h1 {
  font-size: 6vmin;
  line-height: 1.2em;
  margin-right: 15%;
}

.slide-fade-enter-active {
  transition: all .2s ease;
}
.slide-fade-leave-active {
  transition: all .3s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active for <2.1.8 */ {
  transform: translateY(10px);
  opacity: 0;
}
</style>
