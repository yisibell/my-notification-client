<template>
  <div>
    <h1>Notification</h1>
    <p>{{ msg }}</p>
  </div>
</template>

<script setup lang="ts">
import { onMounted, ref } from '@vue/runtime-core'
import { io } from 'socket.io-client'

const msg = ref()

onMounted(() => {
  const socket = io('ws://127.0.0.1:3000')
  socket.on('message', data => {
    msg.value = data
  })
})
</script>

<style scoped>
.logo {
  height: 6em;
  padding: 1.5em;
  will-change: filter;
}
.logo:hover {
  filter: drop-shadow(0 0 2em #646cffaa);
}
.logo.vue:hover {
  filter: drop-shadow(0 0 2em #42b883aa);
}
</style>
