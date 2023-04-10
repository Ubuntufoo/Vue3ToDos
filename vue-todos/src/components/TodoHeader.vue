<script setup>
import { RouterLink } from 'vue-router';
</script>

<template>
  <header>
    <nav class="container-fluid">
      <div class="branding">
        <img src="../assets/redCheckMark.png" alt="Big Red Check Mark" width="80" height="80">
        <h1>To-Do List</h1>
      </div>
      <ul class="nav-routes">
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </ul>
    </nav>
  </header>
</template>

<style lang="scss" scoped>
header {
  background-color: rgba(255, 255, 255, 0.5);

  nav {
    display: flex;
    align-items: center;
    padding: 25px 200px;

    .branding {
      display: flex;
      align-items: center;
      gap: 8px;

      img {
        max-width: 50px;
      }

      h1 {
        font-size: 24px;
      }
    }

    .nav-routes {
      display: flex;
      flex: 1;
      justify-content: flex-end;
      gap: 12px;
      list-style: none;

      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}
</style>

