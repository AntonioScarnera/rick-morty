<template>
    <div>
        <div v-for="(item) in  characterList" :key="item.id">
            ID - {{item.id}} / name - {{item.name}} / status - {{item.status}} / type - {{item.type}} / species - {{item.species}} / image - <img :src="item.image">
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    name: 'GridComponent',
    data(){
        return{
            characterList: [],
            apiPath: 'https://api.sampleapis.com/rickandmorty/'
        }
    },
    mounted(){
        axios.get(this.apiPath + 'characters').then((res)=>{
            this.characterList = res.data;
            console.log(this.characterList);
        })
    }
}
</script>

<style lang="scss" scoped>

</style>