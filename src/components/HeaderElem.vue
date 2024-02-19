<template>
  <nav class="content_line">
    <RouterLink to="/"> Home</RouterLink>
    <RouterLink to="/users">Users</RouterLink>
    <RouterLink to="/profile">Profile</RouterLink>
  </nav>

</template>


<script>

import { RouterLink } from 'vue-router'
export default {
}

</script>

<style>

nav {
  margin-top: 20px;
  display: flex;
  gap: 30px;
  justify-content: flex-end;
}

nav a {
  text-decoration: none;
  color: black;
  font-size: 20px;
  font-weight: 500;
  line-height: 29px;
  letter-spacing: 0px;
  text-align: right;

}
</style>