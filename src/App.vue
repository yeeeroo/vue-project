<script type="module">
import { RouterView } from 'vue-router';

export default {
  // 元件宣告
  components: {
    RouterView,
  },
}
</script>

<template>
  <!-- 觀察你的設計稿 把共用的部分放在此頁面 -->
  <header>
    <RouterLink to="/">home</RouterLink>
    <RouterLink to="/about">about</RouterLink>
    <RouterLink to="/calc">calc</RouterLink>
    <RouterLink to="/todo">todo</RouterLink>
  </header>
  <main>
    <RouterView />
    <!-- <div class="calc">我來自公版</div> -->
  </main>
  <footer>
  </footer>

</template>

<!-- scoped style只影響這支vue -->
<style scoped>
</style>