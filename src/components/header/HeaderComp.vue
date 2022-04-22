<template>
    <div class="d-flex justify-content-between align-imtems-cente p-3 bg_custom">
        <img src="../../assets/img/Netflix-logo-500x281.png" alt="">
        <div class="input-group mb-3 w-25 d-flex align-items-center">
            <input type="text" class="form-control" placeholder="Cerca il tuo film" aria-label="Recipient's username"
                aria-describedby="button-addon2" v-model="ricerca">
            <button class="btn btn-outline-secondary bg-danger text-white" type="submit" id="button-addon2"
                @click.prevent="$emit('funzRicerca', ricerca)" 
            >Avvia Ricerca</button>
        </div>
    </div>
</template>

<script>
    export default {
        name: 'HeaderComp',
        data() {
            return {
                ricerca:''
            }
        },

    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
    img{
        height: 80px;
    }

</style>