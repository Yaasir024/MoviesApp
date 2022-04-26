<template>
  <header>
      <router-link to="/">
        <h1><span>Movies</span>App</h1>
      </router-link>   
  </header>
  <router-view/>
</template>

<script>
import HomeView from '@/views/HomeView.vue'
export default {
  components : {HomeView}
}
</script>


<style>
  @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');

  * {
    padding: 0;
    margin: 0;
    box-sizing: border-box;
  }
  body {
    font-family: 'Inter', sans-serif;
    background: #222;
    color: #fff;
  }
  a {
    text-decoration: none;
  }
  header {
    background: #111;
    padding: 20px 0;
    text-align: center;
  }
  header h1 {
    color: #fff;
    font-size: 28px;
  }
  header h1 span{
    font-weight: bold;
    color: #6366F1;
  }
</style>
