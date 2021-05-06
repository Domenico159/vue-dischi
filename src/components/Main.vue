<template>

  <main>
      <div class="container-custom">
          <div class="row justify-content-center flex-wrap">
              <div v-for="(disk,index) in DiskList.response"
              :key="index"
              class="col-custom">
                  <div class="disk text-center">
                      <img class="mb-3" :src="disk.poster" :alt="disk.author">
                      <h6 class="mb-2">{{ disk.title }}</h6>
                      <div class="text-grey mb-2">{{ disk.author }}</div>
                      <div class="text-grey mb-3">{{ disk.year }}</div>
                      <h6>{{ disk.genre }}</h6>
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
    padding: 0 5px;

    .disk{
   min-height: 330px;
   background:$color-card; 
   margin: 10px;
   padding: 15px;
   color: #fff;
        
        img{
            width: 100%;
        }

        .text-grey{
            color: #ccc;
            font-size: 12px;
            font-weight: 500;
        }
}
}


}


</style>