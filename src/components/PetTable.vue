<template>
  <div>
    <h2>{{ species }} for adoption</h2>
    <b-table striped hover :items="pets">
      <template v-slot:cell(name)="data">
        <router-link :to="`/pet/${species.toLowerCase()}/${data.index}`">
          {{ data.value }}
        </router-link>
      </template>
    </b-table>
  </div>
</template>

<script>
export default {
  props: {
    species: String,
    pets: Array
  }
}
</script>

<style>

</style>
