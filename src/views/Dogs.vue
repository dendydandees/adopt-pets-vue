<template>
  <div>
    <PetTable species="Dogs" :pets="dogs"/>
  </div>
</template>

<script>
import { mapState } from 'vuex'
import PetTable from '@/components/PetTable'

export default {
  computed: {
    ...mapState(['dogs'])
  },
  components: {
    PetTable
  }
}
</script>

<style></style>
