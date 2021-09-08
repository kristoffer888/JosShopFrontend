<template>
    <tr :id="manufacturer.manufacturerId">
      <td style="width: 30px;"><input :id="manufacturer.manufacturerId" type="checkbox" @click="addArray(manufacturer.manufacturerId)"/></td>
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
