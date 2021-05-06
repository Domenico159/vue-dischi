<template>

  <div class="disk">
      
  </div>

</template>

<script>

import axios from 'axios';

export default {
    name:'Disk',
    data(){

        return {
            apiUrl:'https://flynn.boolean.careers/exercises/api/array/music',
            DiskList:[],
            loading:true,
        }
    },
    created(){

        this.getDisk();
        

    },
    methods:{

        getDisk(){

            axios.get(this.apiUrl)

            .then( result => {
                this.DiskList = result.data

                this.loading = false;
            })

            .catch(err =>{
                console.log(err);
            })

        }

    }
}
</script>

<style>

</style>