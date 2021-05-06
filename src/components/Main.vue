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
                      <h6 class="text-genre">{{ disk.genre }}</h6>
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
    min-height: 100vh;
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
   transition: transform 0.3s;
   cursor: pointer;

   &:hover{
       transform: scale(1.1);
   }
        
        img{
            width: 100%;
        }

        .text-grey{
            color: #7c7f84;
            font-size: 12px;
            font-weight: 600;
        }

        h6{
            font-weight: 600;
        }


        .text-genre{
            font-size: 12px;
            font-weight: 600;
        }
}
}


}


@media screen and (min-width:0px) and (max-width:600px){


main .container-custom .col-custom{

    width: calc(100% / 2 );

}

}

@media screen and (min-width:601px) and (max-width:1200px){


main .container-custom .col-custom{

    width: calc(100% / 4 );

}

}



</style>