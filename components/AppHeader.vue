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

<style>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 2rem;
  border-bottom: 1px dotted #666;
}
.header .title {
  font-size: 3rem;
}
.header ul {
  display: flex;
}
.header a {
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

