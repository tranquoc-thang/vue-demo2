<template>
  <nav class="navbar navbar-expand-lg navbar-dark bg-dark">
    <div class="container-fluid">
      <div
        class="collapse navbar-collapse justify-content-center"
        id="navbarNav"
      >
        <ul class="navbar-nav">
          <li class="nav-item">
            <a class="nav-link" aria-current="page" href="#">
              <router-link class="nav-link" :to="{ name: 'Home' }"
                >Home</router-link
              >
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">
              <router-link class="nav-link" :to="{ name: 'Cart' }"
                >Cart</router-link
              >
            </a>
          </li>
          <li class="nav-item">
            <a class="nav-link" href="#">
              <router-link class="nav-link" :to="{ name: 'List' }"
                >List</router-link
              >
            </a>
          </li>
        </ul>
      </div>
    </div>
  </nav>
</template>

<script>
export default {
  name: "Nav",
};
</script>

<style lang="scss" scoped>
a {
  text-decoration: none;
}
</style>
