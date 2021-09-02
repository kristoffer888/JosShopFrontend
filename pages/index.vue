<template>
  <div>
    <h2>Manufacturer List</h2>

    <table id="myTable">
      <tr>
        <th>Manufacturer</th>
        <th>ID</th>
      </tr>
      <AddTable v-for="manufacturer in manufacturers" :key="manufacturer.id" :manufacturer="manufacturer"/>
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
      manufacturers: []
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
  }
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
</style>
