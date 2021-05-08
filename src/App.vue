<template>
  <div id="app">
    
    <!-- Header -->
    <Header />
    <!-- FilterGenders -->
    <FilterGenders 
    @changeGenere="changeGenereCorrent"
    :generi="genersMusical"
    />
    <!-- Main -->
     <Main 
     :allDisk="changeGenereAction"
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
            thisGenere:'',
        }
    },
    created(){
        this.getDisk();
        this.changeGenereCorrent();
        this.thisGenere = 'All'
        
    },
    updated(){
      this.generatedGeners();
    },
    computed:{
      changeGenereAction(){
        if(this.thisGenere == 'All'){
          return this.DiskList
        }
        return this.DiskList.filter(ele =>{
          return ele.genre == this.thisGenere
        })
      }
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
        changeGenereCorrent(genere){
          
          this.thisGenere = genere

        }
    }
}
</script>

<style lang="scss">

@import '~bootstrap/scss/bootstrap';
@import "~@fontsource/montserrat/index.css";
@import "~@fontsource/montserrat/700.css";
@import "@/styles/general";

</style>
