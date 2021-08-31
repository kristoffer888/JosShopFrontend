<template>
  <div>
    <h2>Delete Manufacturer</h2>

    <div>
      <form @submit.prevent="submitForm">
        <label>ID</label>
        <input id="id" v-model="id" type="text"><br>
        <div className="flex w-full mt-8">
          <button
            className="w-full bg-gray-800 hover:bg-grey-900 text-white text-sm py-2 px-4 font-semibold rounded focus:outline-none focus:shadow-outline h-10">
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
      id: ''
    }
  },
  methods: {
    submitForm() {
      console.log(this.id)
      this.$axios.delete('http://localhost:11700/Manufacturer', {data: {
        manufacturerId: this.id
      }}).then(response => {
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
