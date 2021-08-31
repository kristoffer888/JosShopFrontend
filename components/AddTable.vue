<template>
    <tr>
      <td>{{ manufacturer.manufacturerName }}</td>
      <td>{{ manufacturer.manufacturerId }}</td>
    </tr>
</template>

<script>
export default {
  manufacturer: "manufacturer",
  props: ['manufacturer']
}
</script>
