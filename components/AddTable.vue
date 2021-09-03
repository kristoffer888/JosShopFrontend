<template>
    <tr>
      <td style="width: 30px;"><input @click="addArray(manufacturer.manufacturerId)" type="checkbox"/></td>
      <td>{{ manufacturer.manufacturerName }}</td>
      <td>{{ manufacturer.manufacturerId }}</td>
    </tr>
</template>

<script>

export default {
  manufacturer: "manufacturer",
  props: ['manufacturer'],
  data() {
    return {

    }
  },
  methods:{
    addArray(id){
      this.$emit('add-array', id)
    }
  }
}
</script>
