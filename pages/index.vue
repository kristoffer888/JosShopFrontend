<template>
  <div>
    <div style="display: flex; justify-content: space-between;">
      <h2>Manufacturer List</h2>
      <button @click="submitForm()">Delete</button>
    </div>
    <table id="myTable">
      <tr>
        <th></th>
        <th>Manufacturer</th>
        <th>ID</th>
      </tr>

      <AddTable v-for="manufacturer in manufacturers" :key="manufacturer.id" :manufacturer="manufacturer"
                @add-array="addArray"/>
    </table>
  </div>
</template>

<script>
import AddTable from "../components/AddTable"

export default {
  components: {
    AddTable
  },
  data() {
    return {
      manufacturers: [],
      toggleBut: []
    }
  },
  head() {
    return {
      title: "Manufacturer List",
      meta: [
        {
          hid: "description",
          name: "description",
          content: "Joeshop data"
        }
      ]
    };
  },
  async created() {
    const config = {
      headers: {
        'Accept': 'application/json'
      }
    }
    try {
      const res = await this.$axios.get('http://localhost:11700/Manufacturer', config);
      console.log(res.data)
      this.manufacturers = res.data;
    } catch (err) {
      console.log(err)
    }
  },
  methods: {
    addArray(id) {
      console.log(this.toggleBut)
      if (this.toggleBut.includes(id)) {
        this.toggleBut.splice(this.toggleBut.indexOf(id), 1)
      } else {
        this.toggleBut.push(id)
      }
      console.log(this.toggleBut)
      return this.toggleBut
    },
    submitForm() {
      for (let i = 0; i < this.toggleBut.length; i++) {
        this.$axios.delete('http://localhost:11700/Manufacturer', {
          data: {
            manufacturerId: this.toggleBut[i]
          }
        }).then(response => {
          console.log(response)
        }).catch(error => {
          console.log(error)
        })
      }
      this.toggleBut = []
    }
  },
};
</script>

<style>
table {
  font-family: arial, sans-serif;
  border-collapse: collapse;
  width: 100%;
  margin-top: 10px;
}

td, th {
  border: 1px solid #bbbbbb;
  text-align: left;
  padding: 8px;
}

tr:nth-child(even) {
  background-color: #e3e3e3;
}

a {
  display: inline-block;
  background: #666;
  color: #fff;
  padding: 0.3rem 1rem;
  margin-right: 0.5rem;
  border-radius: 5px;
}

a:hover {
  background: #7c7c7c;
}
</style>
