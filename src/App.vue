<script>
import { RouterLink, RouterView } from 'vue-router'
// import HelloWorld from './components/HelloWorld.vue'

export default {
  components: {
    RouterLink,
    RouterView
  },
  data() {
    return {
      count: 0,
    }
  },
}
</script>

<template>
  <!-- 觀察設計稿 把共用的部分放在此頁面 -->
  <header>
    <RouterLink to="/">Home</RouterLink>
    <RouterLink to="/about">About</RouterLink>
    <RouterLink to="/calc">Calc</RouterLink>
    <RouterLink to="/game">Game</RouterLink>
  </header>
  <main>
    主頁樣式
    <!-- count : {{ count }}
    <div>
      <button type="button" @click="count++">++</button>
    </div> -->
    <RouterView />
  </main>
  <footer></footer>
</template>

<style></style>
