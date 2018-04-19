<template>
    <div class="row">
        <div class="col-12">
            <div class="card-columns">
                <app-quote :key="(quote,idx)" v-for="(quote,idx) in quotes" @click.native="deleteQuote(idx)">{{ quote }}</app-quote>
            </div>
        </div>
    </div>
</template>

<script>
    import Quote from './Quote.vue';

    export default {
        props:['quotes'],
        components:{
            appQuote: Quote
        },
        methods:{
            deleteQuote(idx){
                this.$emit('quoteDeleted', idx);
            }
        }
    }
</script>

<style lang="scss">
</style>
