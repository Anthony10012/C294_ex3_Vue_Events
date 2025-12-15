<script setup>
import { RouterLink, RouterView } from 'vue-router'
import EventCard from './components/EventCard.vue'
</script>

<template>
  <div class="navigation">
    <RouterLink to="/">Evénements</RouterLink>|
    <RouterLink to="/About">A propos</RouterLink>
    <RouterView />
  </div>
</template>

<style scoped>
/* Supprimez tous les styles 'nav' existants */

.navigation {
  width: 100%;
  text-align: center; /* Centre le menu */
  padding: 10px 0;
  margin-bottom: 20px; /* Ajoute de l'espace avant les événements */
}

.navigation a {
  color: #3f9e42; /* Couleur verte pour les liens */
  text-decoration: none; /* Enlève le soulignement par défaut */
  font-size: 16px;
}

.navigation a:hover {
  text-decoration: underline; /* Souligne au survol */
}

/* On enlève la bordure qui n'est pas présente dans le design cible */
.navigation a,
.navigation a:first-of-type {
  display: inline-block;
  padding: 0 5px;
  border-left: none;
}
</style>
