<script setup>
import { RouterLink } from 'vue-router';
import { Icon } from '@iconify/vue';
</script>

<template>
  <header>
    <nav class="container-fluid">
      <div class="branding">
        <img src="../assets/redCheckMark.png" alt="Big Red Check Mark" width="80" height="80">
        <h1>To-Do List</h1>
      </div>
      <ul class="nav-routes">
        <RouterLink to="/">
          <Icon icon="material-symbols:home-outline" width="70" />
        </RouterLink>
        <RouterLink to="/about">
          <Icon icon="mdi:about-variant" width="70" />
        </RouterLink>
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
    justify-content: space-between;
    padding: 25px 200px;

    .branding {
      color: #dd3e54;
      display: flex;
      align-items: center;
      gap: 10px;

      img {
        max-width: 50px;
      }

      h1 {
        font-size: 36px;
      }
    }

    .nav-routes {
      display: flex;
      justify-content: flex-end;
      gap: 30px;
      list-style: none;
      padding: 10px;

      a {
        text-decoration: none;
        color: inherit;
      }
    }
  }
}
</style>

