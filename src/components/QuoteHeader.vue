<template>
<div>
    <div id="logo">
   <img src="../assets/quotes.svg" alt="quotes svg" />
   <h2>{{ logo }}</h2>
   </div>
   <h3>{{ date }}</h3>
 </div>
</template>

<script>
export default {
    name: "quote-header",
    props: [
        "logo", 
         "date"]
}
</script>

<style scoped>
div {
    display: flex;
    justify-content: space-between;
    align-items: center;
}
#logo {
    display: flex;
    align-items: center;
}
img {
    height: 2em;
    margin-right: 1em;;
}
</style>