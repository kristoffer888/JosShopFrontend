<template>
    <div class="main-block">
      <h1>Create Manufacturer</h1>
      <form @submit.prevent="submitForm">
        <hr>
        <label class="icon" for="name"><i class="fas fa-industry"></i></label>
        <input id="name" ref="name" v-model="name" type="text" name="name"
               style="height: 44.2px; margin-top: 10px; width: 228px;"
               placeholder="Manufacturer Name" required @input="removeResponse"/>
        <p id="succText"></p>
        <div class="btn-block">
          <button style="background: #7c7c7c">Submit</button>
        </div>
      </form>
    </div>
</template>

<script>
export default {
  data() {
    return {
      name: ''
    }
  },
  mounted() {
    this.$refs.name.focus()
  },
  methods: {
    removeResponse() {
      document.getElementById('succText').innerText = '';
    },
    submitForm() {
      console.log(this.name)
      this.$axios.post('http://localhost:11700/Manufacturer', {

        manufacturerName: this.name
      }).then(response => {
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
