<template>
  <form class="pt-5 d-flex justify-content-center">
      <label for="disks">Choose a car:</label>
      <select class="ms-3" id="disks" name="disks">
        <option value="all">All</option>
        <option v-for="(element,index) in generi "
        :key="index"
        :value="element">{{ element }}</option>
      </select>
  </form>
</template>

<script>
export default {
    name:'FilterGenders',
    props:['generi']
}
</script>

<style scoped lang="scss">
  @import '@/styles/vars.scss';
form{

    background: $bg-color;
    color: #fff;
}

</style>