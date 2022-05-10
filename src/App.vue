<template>
  <div id="app">
    <header-component :message="titolo"/>
    <main>
      <grid-component/>
    </main>

  </div>
</template>

<script>
import HeaderComponent from './components/HeaderComponent.vue'
import GridComponent from './components/GridComponent.vue'


export default {
  name: 'App',
  components: {
    HeaderComponent,
    GridComponent,

    
  },
  data(){
    return{
      titolo: 'Rick e Morty'
    }
  }
}
</script>

<style lang="scss">
@import "@/assets/style/general.scss";

</style>
