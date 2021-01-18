<template>
<div id="footer">
    <div id="author-info">
    <h5>quote by</h5>
   <h2>{{ author }}</h2>
   </div>
    <button v-on:click="generateQuote">New Quote</button>
 </div>
</template>

<script>
import { eventBus } from "@/main.js";
export default {
    name: "quote-footer",
    props: ["author"],
    methods: {
        generateQuote: function() {
            eventBus.$emit('new-quote');
        }
    }
  }


</script>

<style scoped>

#footer {
    display: flex;
    justify-content: space-between;
    align-items: center;
    position: fixed;
    bottom: 0;
    margin-bottom: 2em;
   
    width: 93vw;
}

#author-info {
    display: auto;
}

h5 {
    margin-bottom: -0.5em;
}

button {
    outline: none;
    box-shadow: none;
    width: 10em;
    padding: 0.3em;
    border-radius: 30px;
    font-size: 1em;
    font-weight: bold;
    border: 2px, solid,  #181818;
    background-color:transparent;
    color:  #181818;
  
}

button:hover {
    background-color:  #181818;
    color: white;
}

button:active {
     transform: scale(0.99);
}

</style>