<template>
  <div class="home-view-container">
    <h1>Adopt a new best friend</h1>
    <p>Total animals : {{ animalsCount }}</p>
    <p>Total cats : {{ getAllCats.length }}</p>
    <p>Total dogs : {{ getAllDogs.length }}</p>
    <b-button @click="togglePetForm" variant="primary">Add New Pet</b-button>

    <b-row>
      <b-col cols="4" class="mx-auto my-4">
        <b-form @submit.prevent="handleSubmit" v-if="showPetForm">
          <b-form-group class="text-left" id="input-group-2" label="Pets Name:" label-for="input-2">
            <b-form-input
              id="input-2"
              type="text"
              v-model="formData.name"
              required
              placeholder="Enter name"
            ></b-form-input>
          </b-form-group>

          <b-form-group class="text-left" id="input-group-3" label="Species:" label-for="input-3">
            <b-form-select
              id="input-3"
              v-model="formData.species"
              :options="['cats', 'dogs']"
              required
            ></b-form-select>
          </b-form-group>

          <b-form-group class="text-left" id="input-group-2" label="Pets Age:" label-for="input-2">
            <b-form-input
              id="input-2"
              type="number"
              v-model="formData.age"
              required
              placeholder="Enter age"
            ></b-form-input>
          </b-form-group>

          <b-button type="submit" variant="primary">Submit</b-button>
        </b-form>
      </b-col>
    </b-row>
  </div>
</template>

<script>
// @ is an alias to /src
import { mapActions, mapGetters } from 'vuex'

export default {
  data () {
    return {
      showPetForm: false,
      formData: {
        name: '',
        age: 0,
        species: null
      }
    }
  },
  computed: {
    ...mapGetters([
      'animalsCount',
      'getAllCats',
      'getAllDogs'
    ])
  },
  methods: {
    ...mapActions([
      'addPet'
    ]),
    togglePetForm () {
      this.showPetForm = !this.showPetForm
    },
    handleSubmit () {
      const { species, name, age } = this.formData
      const payload = {
        species,
        pet: {
          name,
          age,
          species
        }
      }
      this.addPet(payload)

      // reset form after submit
      this.formData = {
        name: '',
        age: 0,
        species: null
      }
    }
  }
}
</script>
