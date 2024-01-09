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
    <RouterLink to="/calc">計算機</RouterLink>
    <RouterLink to="/todoList">待辦清單</RouterLink>
    <RouterLink to="/picUpload">上傳照片</RouterLink>
    <RouterLink to="/weatherApi">天氣預報</RouterLink>
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