<script setup lang="ts">
import Hero from '@/components/Hero.vue';
import HomeCards from '@/components/HomeCards.vue';
import JobListings from '@/components/JobListings.vue';
</script>

<template>
  <Hero title="Becoming a Powerfull Vue Dev " sub-title="And find the Vue job that fits your skills and needs" />
  <HomeCards />
  <JobListings :limit="3" :show-button="true" />
</template>