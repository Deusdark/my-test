<template>
  <div>Hello bienvenue sur le meetup Nuxt3 Paris</div>

  <div v-if="error">Une error est survenue</div>
  <div v-else-if="pending">En cours de chargement</div>
  <div v-else>
    <div v-for="product in data">
      {{ product.title }}
    </div>
  </div>
</template>

<script setup>
const config = useRuntimeConfig();

const { data, error } = await useAsyncData("products", () =>
  fetch(`${config.STORE_URL}/products`).then((response) => response.json())
);
</script>
