<template>
  <div class="card mb-4">
    <img :src="project.image" class="card-img-top" :alt="project.title">
    <div class="card-body">
      <h5 class="card-title">{{ project.title }}</h5>
      <p class="card-text">{{ project.description }}</p>
    </div>
  </div>
</template>

<script setup>
defineProps({
  project: Object
})
</script>
