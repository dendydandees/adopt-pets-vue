<template>
  <div class="text-capitalize">
    <h3>{{ animal.name }} ({{this.$route.params.species}})</h3>
    <p>age: {{ animal.age }} years old</p>
    <p>breed: {{ animal.breed }}</p>
  </div>
</template>

<script>
import { mapState } from 'vuex'

export default {
  data () {
    return {
      animal: {}
    }
  },
  computed: {
    ...mapState([
      'cats',
      'dogs'
    ])
  },
  mounted () {
    const animal = this[this.$route.params.species][this.$route.params.id]
    this.animal = animal
  }
}
</script>

<style>

</style>
