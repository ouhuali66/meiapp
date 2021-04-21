<template>
  <div>
    <div style="background: yellow">film</div>
    <film-header></film-header>
    <router-view></router-view>
  </div>
</template>

<script>
import filmHeader from './film/FilmHeader.vue'

export default {
  components: {
    filmHeader
  }
}
</script>
<style scoped>
*{
  margin: 0;
  padding: 0;
}
ul {
  list-style: none;
  display: flex;
}
li {
  flex:1;
}
.active {
  color: pink
}
</style>
