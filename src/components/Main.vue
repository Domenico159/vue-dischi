<template>

  <main>
      <div class="container-custom">
          <div class="row justify-content-center flex-wrap">
              <div v-for="(disk,index) in DiskList.response"
              :key="index"
              class="col-custom">
                  <div class="disk">
                      <div class="img"></div>
                  </div>
              </div>
          </div>
      </div>
  </main>

</template>

<script>

import axios from 'axios';

export default {
    name:'Main',
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

<style scoped lang="scss">

@import '@/styles/vars.scss';

main{
    padding:80px 20px 15px 20px;
    background: $bg-color;
}

.container-custom{

    max-width: 1450px;
    margin: 0 auto;

.col-custom{

    width: calc(100% / 8 );

    .disk{
   height: 300px;
   background:$color-card; 
   margin: 10px;
}
}


}


</style>