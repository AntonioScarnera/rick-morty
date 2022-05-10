<template>
    <div>
        <div class="input-group mb-3">


            <select name="genre" id="genre" v-model="inputText" @change="search">
                <option value="">all</option>
                <option :value="specie" v-for="(specie, index) in characterSpecies" :key="index">{{specie}}</option>
            </select>
            
            <button class="btn btn-outline-secondary" type="button" @click.prevent="reset">reset</button>
        </div>
    </div>
</template>

<script>
export default {
    name: 'SearchBarComponent',
    data(){
        return{
            inputText: '',
        }
    },
    methods:{
        reset(){
            this.inputText = ''
            this.$emit('mysearch', this.inputText)
        },
        search(){
            this.$emit('mysearch',this.inputText)
            //this.inputText = ''
        }
    },
    props:['characterSpecies']
}
</script>

<style lang="scss">

</style>