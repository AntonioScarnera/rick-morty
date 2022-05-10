<template>
    <section class="container">

        <search-bar-component @mysearch="setSearchText($event)" :characterSpecies="species"/>

        <loader-component v-if="loading" />

        <div class="row gy-3">
            <div v-for="character in  filteredList" :key="character.id" class="col-6 col-md-4 col-lg-3">
                <card-component :item="character" />
            </div>
        </div>
        <footer-component :len="filteredList.length"/>
    </section>
</template>

<script>

import LoaderComponent from './LoaderComponent.vue'
import CardComponent from './CardComponent.vue'
import FooterComponent from './FooterComponent.vue'
import axios from 'axios';
import SearchBarComponent from './SearchBarComponent.vue';


export default {
    name: 'GridComponent',
    components:{
        LoaderComponent,
        CardComponent,
        FooterComponent,
        SearchBarComponent,
        } ,
    data(){
        return{
            characterList: [],
            searchText: '',
            apiPath: 'https://api.sampleapis.com/rickandmorty/',
            loading: false,

            species: []
        }
    },
    methods:{
        setSearchText(text){
            this.searchText = text;
        }
    },
    computed: {
        filteredList(){
            if(this.searchText === '') return this.characterList;

            
            return this.characterList.filter((element)=>element.species === this.searchText)
        }
    },
    created(){
        this.loading = true;
        axios.get(this.apiPath + 'characters').then((res)=>{
            this.characterList = res.data;

            this.characterList.forEach((el)=>{
                if(!this.species.includes(el.species)){
                    this.species.push(el.species);
                }
            })
    console.log(this.species)
            this.loading = false;
        }).catch((error)=>{
            console.log(error);
            this.loading = false;
        })
    }

}
</script>

<style lang="scss" scoped>

</style>