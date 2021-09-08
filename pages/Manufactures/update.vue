<template>
    <div class="main-block">
      <h1>Update Manufacturer</h1>
      <form @submit.prevent="submitForm">
        <hr>
        <label class="icon" for="id"><i class="fa-solid fa-id-card"></i></label>
        <input id="id" ref="id" v-model="id" required style="height: 44.2px; margin-top: 10px; width: 228px;"
               placeholder="Manufacturer ID" name="name" type="text" @input="removeResponse"/>
        <label class="icon" for="name"><i class="fas fa-industry"></i></label>
        <input id="name" v-model="name" type="text" required style="height: 44.2px; margin-top: 10px; width: 228px;"
               placeholder="Manufacturer Name" name="name" @input="removeResponse()"/>
        <p id="succText"></p>
        <div class="btn-block">
          <button>Submit</button>
        </div>
      </form>
  </div>
</template>

<script>

export default {
  data() {
    return {
      id: '',
      name: ''
    }
  },
  mounted() {
    this.$refs.id.focus()
  },
  methods: {
    removeResponse() {
      document.getElementById('succText').innerText = '';
    },
    submitForm() {
      console.log(this.name)
      this.$axios.put('http://localhost:11700/Manufacturer', {
        manufacturerId: this.id,
        manufacturerName: this.name
      }).then(response => {
        document.getElementById("id").value = "";
        document.getElementById("name").value = "";
        document.getElementById("succText").style.color = "green"
        document.getElementById("succText").innerText = "Success";
        console.log(response)
      }).catch(error => {
        document.getElementById("succText").style.color = "red"
        document.getElementById("succText").innerText = "Error";
        console.log(error)
      })
    }
  }
};
</script>
<style>
</style>
