<template>

  <main>

      <section class="container">
          <div class="row">
          <div class="col-6 col-md-4 col-lg-3">
              <Disk />
          </div>
      </div>
      </section>

  </main>

</template>

<script>
import Disk from './Disk.vue';
export default {
    name:'Main',
    components: {
        Disk,
    }
}
</script>

<style scoped lang="scss">


</style>