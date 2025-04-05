<template>
  <nav>
    <RouterLink to="/">Accueil</RouterLink>
    <RouterLink to="/login">Login</RouterLink>
    <RouterLink v-if="isAuthenticated" to="/profile">Profil</RouterLink>
    <RouterLink v-if="isAuthenticated && $zitadel.hasRole('admin')" to="/admin"
      >Admin</RouterLink
    >

    <button v-if="isAuthenticated" @click="$zitadel.oidcAuth.signOut()">
      Se déconnecter
    </button>
  </nav>

  <router-view />
</template>

<script setup lang="ts">
import { ref, onMounted } from "vue";

const isAuthenticated = ref(false);

onMounted(async () => {
  const zitadel = (window as any).$zitadel;
  if (zitadel) {
    isAuthenticated.value = await zitadel.oidcAuth.isAuthenticated();
  }
});
</script>

<style>
.game-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 20px;
  background-color: #c3c3c3;
  min-height: 100vh;
  padding: 20px;
}

h1 {
  font-family: "Courier New", Courier, monospace;
  color: #2d2d2d;
  text-shadow: 3px 3px #9ba657;
  margin: 0;
}
</style>
