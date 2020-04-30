<template>
  <div id="app">
    <p>{{ message }}</p>
    <ul>
      <li v-for="item in items" :key="item.id">{{ item }}</li>
    </ul>
    <button @click="handleClick">クリックします</button>
    <br>
    <input v-model="message">
    <br>
    <button @click="show=!show">切り替えボタン</button>
    <transition>
      <p v-if="show">Hello〜</p>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      message: 'ホームです',
      items: [
        'おっぱい', 'てぃんぽ', 'ああん'
      ],
      show: false
    }
  },
  methods: {
    handleClick() {
      alert('こんにちは')
    }
  }
}
</script>

<style>
.v-enter-active, .v-leave-active {
  transition: opacity 1s;
}
.v-enter, .v-leave-to {
  opacity: 0;
}
button {
  cursor: pointer;
}
</style>
