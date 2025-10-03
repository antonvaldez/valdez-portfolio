<template>
  <div class="container my-5" id="projects">
    <h2 class="mb-4">My Web Developer Projects</h2>
    <div class="row row-cols-1 row-cols-md-3 g-4">
      <div class="col" v-for="project in projects" :key="project.id">
        <div class="card h-100 project-card">
          <img :src="project.image" class="card-img-top" :alt="project.title">
          <div class="card-body d-flex flex-column">
            <h5 class="card-title">{{ project.title }}</h5>
            <p class="card-text flex-grow-1">{{ project.description }}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import projectsData from '../data/projects.json'

export default {
  name: "Projects",
  data() {
    return {
      projects: projectsData
    }
  }
}
</script>

<style scoped>
#projects h2 {
  text-align: center;
  font-size: 2.5rem;
  margin-bottom: 2rem;
}

.card img {
  height: 200px;
  object-fit: cover;
}

.card-body {
  display: flex;
  flex-direction: column;
}

/* New: change the card background color */
.project-card {
  background-color: #F5F0E1; /* you can change this color */
}
</style>
