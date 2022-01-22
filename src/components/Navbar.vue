<template>
  <nav class="cyan darken-2 padding">
    <div class="nav-wrapper">
      <router-link to="/" class="brand-logo">Tasks</router-link>
      <ul class="right hide-on-med-and-down">
        <router-link
        tag="li"
        to="/"
        exact
        active-class="active"
        >
          <a href="#">Create</a>
        </router-link>
        <router-link
        tag="li"
        to="/list"
        exact
        active-class="active"
        >
          <a href="#">List</a>
        </router-link>
      </ul>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Navbar"

}
</script>

<style scoped>
.padding {
  padding: 0 40px;
}
</style>