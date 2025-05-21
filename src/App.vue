<script setup>
import { ref, computed } from 'vue'
import EnemyCard from './components/EnemyCard.vue'
//import playerCard from './components/PlayerCard.vue'

const img_0_04 = new URL('./assets/0_04.jpg', import.meta.url).href
const img_0_06 = new URL('./assets/0_06.jpg', import.meta.url).href

class Enemy {
  constructor(name, image, difficulty, health, actions) {
    this.name = name
    this.image = image
    this.difficulty = difficulty
    this.health = health
    this.actions = actions
  }
}
function createEnemyCard(front, back) {
  return {
    side: Math.random() > 0.5 ? 'front' : 'back',
    enemy: { front, back },
  }
}
let enemyCards = ref([
  createEnemyCard(
    new Enemy('野猪战车', img_0_04, 4.0, 6, []),
    new Enemy('山猫战车', img_0_06, 2.0, 4, []),
  ),
  createEnemyCard(
    new Enemy('野猪战车', img_0_04, 4.0, 6, []),
    new Enemy('山猫战车', img_0_06, 2.0, 4, []),
  ),
  createEnemyCard(
    new Enemy('野猪战车', img_0_04, 4.0, 6, []),
    new Enemy('山猫战车', img_0_06, 2.0, 4, []),
  ),
  createEnemyCard(
    new Enemy('野猪战车', img_0_04, 4.0, 6, []),
    new Enemy('山猫战车', img_0_06, 2.0, 4, []),
  ),
  createEnemyCard(
    new Enemy('野猪战车', img_0_04, 4.0, 6, []),
    new Enemy('山猫战车', img_0_06, 2.0, 4, []),
  ),
  createEnemyCard(
    new Enemy('野猪战车', img_0_04, 4.0, 6, []),
    new Enemy('山猫战车', img_0_06, 2.0, 4, []),
  ),
])
enemyCards.value.sort(() => Math.random() - 0.5)
const enemy_list = computed(() => enemyCards.value.map((card) => card.enemy[card.side]))
</script>

<template>
  <div id="app">
    <div class="container">
      <div class="enemy_area" v-for="(enemy, idx) of enemy_list" :key="idx">
        <EnemyCard :enemy="enemy" />
      </div>

      <div class="player_area">
        <div class="card" id="LandshipHel"></div>
        <div class="card" id="Cannon"></div>
        <div class="card" id="Sponsons"></div>
      </div>
    </div>
  </div>
</template>
