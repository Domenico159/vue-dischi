<template>
  <header>
      <img src="@/assets/assets-vue-dischi/logo.png" alt="">
  </header>
</template>

<script>
export default {
    name:'Header',
}
</script>

<style scoped lang="scss">

@import '@/styles/vars.scss';

header{
    background: $color-card;

    img{
        width: 50px;
        margin: 5px;
    }
}

</style>