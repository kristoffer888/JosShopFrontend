<template>
  <header class="header">
    <h1 class="title">Joeshop</h1>
    <ul>
      <li>
        <nuxt-link to="/">Manufacturer List</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/Manufactures/create">Create</nuxt-link>
      </li>
      <li>
        <nuxt-link to="/Manufactures/update" style="margin: 0">Update</nuxt-link>
      </li>
    </ul>
  </header>
</template>

<script>
export default {
  name: "AppHeader"
}
</script>
