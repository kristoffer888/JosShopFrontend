<template>
  <div>
    <h2>Create Manufacturer</h2>

    <div>
      <form @submit.prevent="submitForm">
        <label>Name</label>
        <input id="name" v-model="name" type="text"><br>
        <div class="flex w-full mt-8">
          <button
            class="w-full bg-gray-800 hover:bg-grey-900 text-white text-sm py-2 px-4 font-semibold rounded focus:outline-none focus:shadow-outline h-10">
            Submit
          </button>
        </div>
      </form>
    </div>

  </div>
</template>

<script>

export default {
  data() {
    return {
      name: ''
    }
  },
  methods: {
    submitForm() {
      console.log(this.name)
      this.$axios.post('http://localhost:11700/Manufacturer', {

        manufacturerName: this.name
      }).then(response => {
        alert("Succes")
        console.log(response)
      }).catch(error => {
        console.log(error)
      })
    }
  }
};
</script>
<style>
</style>
