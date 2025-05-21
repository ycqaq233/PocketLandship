<template>
  <img :src="enemy.image" />
</template>
<script setup>
defineProps({
  enemy: Object,
})
</script>
