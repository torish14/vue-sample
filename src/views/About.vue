<template>
  <div class="about">
    <p>{{ width }}の半分は{{ halfWidth }}</p>

    <p>{{ halfPoint.x }}</p>
    <p>{{ halfPoint.y }}</p>

    <input v-model.number="budget"> 円以下に絞り込む
    <input v-mode.number="limit"> 件を表示
    <p>{{ matched.length }} 件中 {{ limited.length }} 件を表示中</p>
    <ul>
      <li v-for="item in limited" :key="item.id">{{ item.name }}{{ item.price }}円</li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      width: 800,
      height: 600,
      budget: 300,
      limit: 2,
      list: [
        { id: 1, name: 'りんご', price: 100 },
        { id: 2, name: 'ばなな', price: 200 },
        { id: 3, name: 'いちご', price: 300 },
        { id: 4, name: 'おれんじ', price: 400 },
        { id: 5, name: 'めろん', price: 500 }
      ]
    }
  },
  computed: {
    halfWidth() {
      return this.width / 2
    },
    halfHeight() {
      return this.height / 2
    },
    halfPoint() {
      return {
        x: this.halfWidth,
        y: this.halfHeight
      }
    },
    matched() {
      return this.list.filter(function(el) {
        return el.price <= this.budget
      }, this)
    },
    limited() {
      return this.matched.slice(0, this.limit)
    }
  }
}
</script>

<style>

</style>
