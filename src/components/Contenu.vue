<template>
  <div class="container">
    <twitter></twitter>
  </div>
</template>
<script>
import Twitter from './Twitter.vue'
export default {
  name: 'Contenu',
  data: function () {
    return {

    }
  },
  components: {
    'twitter': Twitter,
  }
}
</script>
<style scoped>

</style>