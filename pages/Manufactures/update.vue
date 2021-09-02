<template>
  <div>
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
html, body {
  display: flex;
  justify-content: center;
  height: 100%;
}

body, div, h1, form, input, p {
  padding: 0;
  margin: 0;
  outline: none;
  font-family: Roboto, Arial, sans-serif;
  font-size: 16px;
  color: #666;
}

h1 {
  padding: 10px 0;
  font-size: 32px;
  font-weight: 300;
  text-align: center;
}

p {
  font-size: 12px;
}

hr {
  color: #a9a9a9;
  opacity: 0.3;
}

.main-block {
  max-width: 340px;
  padding: 10px 0;
  margin: auto;
  border-radius: 5px;
  border: solid 1px #ccc;
  box-shadow: 1px 2px 5px rgba(0, 0, 0, .31);
  background: #ebebeb;
}

form {
  margin: 0 30px;
}

label.icon {
  margin: 0;
  border-radius: 5px 0 0 5px;
  width: 46px;
}

.icon {
  display: inline-block;
  padding: 9.3px 15px;
  box-shadow: 1px 2px 5px rgba(0, 0, 0, .09);
  background: #666;
  color: #fff;
  text-align: center;
}

.btn-block {
  margin-top: 10px;
  text-align: center;
}

button {
  width: 100%;
  padding: 10px 0;
  margin: 10px auto;
  border-radius: 5px;
  border: none;
  background: #666;
  font-size: 14px;
  font-weight: 600;
  color: #fff;
}

button:hover {
  background: #7c7c7c;
}
</style>
