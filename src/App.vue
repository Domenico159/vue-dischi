<template>
  <div id="app">
    
    <!-- Header -->
    <Header />
    <!-- FilterGenders -->
    <FilterGenders 
    :generi="genersMusical"
    />
    <!-- Main -->
     <Main 
     :allDisk="DiskList"
     />
  </div>
</template>

<script>
import Header from '@/components/Header.vue';
import Main from '@/components/Main.vue';
import FilterGenders from '@/components/FilterGenders.vue';
import axios from 'axios';

export default {
  name: 'App',
  components: {
    Header,
    Main,
    FilterGenders,
  },
  data(){

        return {
            apiUrl:'https://flynn.boolean.careers/exercises/api/array/music',
            DiskList:[],
            loading:true,
            genersMusical:[],
        }
    },
    created(){
        this.getDisk();
        
    },
    updated(){
      this.generatedGeners();
    },
     methods:{

        getDisk(){

            axios.get(this.apiUrl)

            .then( result => {
                this.DiskList = result.data.response
                this.loading = false;
            })

            .catch(err =>{
                console.log(err);
            })

        },
        generatedGeners(){

          this.DiskList.forEach((element) =>{
           
           if(!this.genersMusical.includes(element.genre)){
             this.genersMusical.push(element.genre);
           }

          })

        },
    }
}
</script>

<style lang="scss">

@import '~bootstrap/scss/bootstrap';
@import "~@fontsource/montserrat/index.css";
@import "~@fontsource/montserrat/700.css";
@import "@/styles/general";

</style>
