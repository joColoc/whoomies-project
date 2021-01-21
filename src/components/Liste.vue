<template>
  <div>
    <ul class="list-unstyled">
      <li v-for="(film, index) in myArr" v-bind:key="index" >
        {{ film.titre }}
        {{ film.date }}
        </li>
    </ul>
    <p v-on:click="supprFilm()">Supprime le fil</p>
  </div>
</template>
<script>
export default {
  name: 'Liste',
  data() {
    return {
      fruits: ['Orange','Papaye','Fraise'],
      myArrs: this.myArr
    }
  },
  props: ['myArr'],
  methods: {
    supprFilm () {
      this.myArrs.pop()
    }
  }
}
</script>
<style scoped>

</style>