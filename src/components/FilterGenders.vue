<template>
  <form class="pt-5 d-flex justify-content-center">
      <label for="disks">Choose a car:</label>
      <select v-model="selected"
      @change="$emit('changeGenere', selected)"
      class="ms-3" id="disks" name="disks">
        <option value="All">All</option>
        <option v-for="(element,index) in generi "
        :key="index"
        :value="element">{{ element }}</option>
      </select>
  </form>
</template>

<script>
export default {
    name:'FilterGenders',
    props:['generi'],
    data(){
        return {
            selected:'All',
        }
    },
}
</script>

<style scoped lang="scss">
  @import '@/styles/vars.scss';
form{

    background: $bg-color;
    color: #fff;
}

</style>