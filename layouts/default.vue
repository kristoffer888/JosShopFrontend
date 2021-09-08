<template>
  <div class="app dark">
    <div class="container">
      <AppHeader/>
      <nuxt/>
    </div>
  </div>
</template>

<script>
import AppHeader from "../components/AppHeader";

export default {
  components: {
    AppHeader
  },
  data() {
    return {
      mode: 'dark'
    }
  },
};
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body, html {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  font-size: 1rem;
  line-height: 1.6;
}

#__nuxt {
  width: 100%;
  height: 100%;
}

#__layout {
  width: 100%;
  height: 100%;
}

.app {
  width: 100%;
  min-height: 100%;
  background: #F3F3F3;
  color: #152028;
}

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
}

form {
  margin: 0 30px;
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
  color: #535353;
}

.main-block {
  max-width: 340px;
  padding: 10px 0;
  margin: auto;
  border-radius: 5px;
  border: solid 1px #ccc;
  box-shadow: 1px 2px 5px rgba(0, 0, 0, .31);
  background: #535353;
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
  background: white;
  color: #535353;
  text-align: center;
}

button {
  display: inline-block;
  background: #535353;
  color: white;
  border-radius: 5px;
  width: 100%;
  padding: 10px 0;
  margin: 10px auto;
  border: none;
  font-size: 14px;
  font-weight: 600;
}

button:hover {
  background: #7c7c7c;
}

.btn-block {
  margin-top: 10px;
  text-align: center;
}

.dark {
  background: #192734;
  color: white;
}

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
  background: #535353;
  color: white;
  padding: 0.3rem 1rem;
  margin-right: 0.5rem;
  border-radius: 5px;
}

a:hover {
  background: #7c7c7c;
}

a {
  color: white;
  text-decoration: none;
}

ul {
  list-style: none;
}

.container {
  width: 800px;
  height: 100%;
  margin: auto;
  overflow: hidden;
}

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
  color: white;
  background-color: #535353;
}
</style>
