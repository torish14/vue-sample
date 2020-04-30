<template>
  <div>
    <ul>
      <li v-for="(item, index) in list" :key="item.id" style="margin-top: 10px;">
        ID. {{ item.id }} {{ item.name }} HP. {{ item.hp }}
        <span v-if="item.hp < 50 && item.hp > 0">瀕死❗</span>
        <span v-if="item.hp <= 0">倒した❗</span>
        <button @click="defaultAttack(index)" style="background-color: skyblue; color: white; margin-right: 5px; font-weight: bold;">通常攻撃</button>
        <button @click="criticalAttack(index)" style="background-color: orange; color: white; margin-right: 5px; font-weight: bold;">クリティカルヒット</button>
        <button @click="deathBlow(index)" style="background-color: red; color: white; font-weight: bold;">必殺技</button>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        { id: 1, name: 'スライム', hp: 100 },
        { id: 2, name: 'ゴブリン', hp: 200 },
        { id: 3, name: 'ドラゴン', hp: 500 },
        { id: 4, name: 'カオスデビルドラゴン', hp: 800 },
        { id: 5, name: 'カオスエンペラードラゴン', hp: 1000 }
      ]
    }
  },
  methods: {
    defaultAttack(index) {
      this.list[index].hp -= 20
    },
    criticalAttack(index) {
      this.list[index].hp -= 50
    },
    deathBlow(index) {
      this.list[index].hp -= 1000
    }
  }
}
</script>

<style>

</style>
