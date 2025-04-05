<script lang="ts">
import { defineComponent } from "vue";

export default defineComponent({
  computed: {
    user() {
      return (this.$zitadel.oidcAuth as any).userProfile;
    },
    claims() {
      if (this.user) {
        return Object.keys(this.user).map((key) => ({
          key,
          value: this.user[key],
        }));
      }
      return [];
    },
  },
});
</script>

<template>
  <div class="profile">
    <h1>Profil utilisateur</h1>
    <ul>
      <li v-for="claim in claims" :key="claim.key">
        <strong>{{ claim.key }}:</strong> {{ claim.value }}
      </li>
    </ul>
  </div>
</template>
