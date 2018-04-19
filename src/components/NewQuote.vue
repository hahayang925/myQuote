<template>
    <div class="row my-3">
         <form class="col-md-6 m-auto">
            <div class="form-group">
                <label>Quote</label>
                <textarea class="form-control" rows="3" v-model="quote"></textarea>
            </div>
            <button class="btn btn-primary" @click.prevent="createNew">Add Quote</button>
        </form>
    </div>
</template>

<script>
    export default {
        data(){
            return {
                quote: ''
            }
        },
        methods:{
            createNew(){
                if(this.quote.trim() === ''){
                    alert('New quote can not be blank!');
                    return;
                }
                this.$emit('quoteAdd', this.quote);
                this.quote = '';
            }
        }
    }
</script>

<style lang="scss">

</style>
