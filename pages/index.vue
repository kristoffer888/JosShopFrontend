<template>
  <div>
    <div style="display: flex; justify-content: space-between;">
      <h2>Manufacturer List</h2>
      <button style="margin: 0; width: 82px" @click="joe()">Delete</button>
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
import swal from 'sweetalert';
import Vue from "vue";
import VueDarkMode from "@growthbunker/vuedarkmode";
import AddTable from "../components/AddTable"

Vue.use(VueDarkMode);

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
    joe() {
      if (this.toggleBut.length > 0)
        swal({
          title: "Are you sure?",
          text: "Once deleted, you will not be able to recover the data!",
          icon: "warning",
          buttons: true,
          dangerMode: true,
        })
          .then((willDelete) => {
            if (willDelete) {
              this.submitForm()
            }
          });
    },

    addArray(id) {
      if (this.toggleBut.includes(id)) {
        this.toggleBut.splice(this.toggleBut.indexOf(id), 1)
      } else {
        this.toggleBut.push(id)
      }
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
        document.getElementById(this.toggleBut[i]).remove()
      }
      this.toggleBut = []
      this.$nuxt.refresh()
    }
  },
};
</script>
