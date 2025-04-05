<template>
  <div class="home">
    <h1>Bienvenue sur le jeu Snake</h1>
    <SnakeGame />
  </div>
</template>

<script setup lang="ts">
import SnakeGame from "../components/SnakeGame.vue";
</script>

<style>
.home {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 2rem;
}
</style>
