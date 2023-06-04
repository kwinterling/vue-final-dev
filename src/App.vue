<script setup>
import { RouterLink, RouterView } from 'vue-router'
import axios from 'axios'
</script>

<template>
  <header>
    
    <div>
     
      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
        <RouterLink to="/jobs">Jobs</RouterLink>
        <RouterLink to="/jobsearch">Job Search</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView />
</template>

<style scoped>



</style>
