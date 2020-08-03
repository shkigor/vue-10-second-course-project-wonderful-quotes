<template>
    <div class="row">
        <app-quote v-for="(quote, index) in quotes" :key="index">{{ quote }}</app-quote>
    </div>
</template>

<script>
import Quote from './Quote';

export default {
    name: "QuoteGrid",
    props: ['quotes'],
    components: {
        appQuote: Quote
    }
}
</script>

<style scoped>

</style>