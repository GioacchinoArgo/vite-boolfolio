<script>
import AppHeader from './components/AppHeader.vue';
import ProjectsList from './components/projects/ProjectsList.vue';
import axios from 'axios';
const endpoint = 'http://localhost:8000/api/projects/';

export default {
  name: 'Boolfolio',
  components: { AppHeader, ProjectsList },
  data: () => ({ projects: [] }),
  methods: {
    fetchProjects() {
      axios.get(endpoint).then(res => {
        this.projects = res.data;
      })
    }
  },
  created() {
    this.fetchProjects();
  }
};
</script>

<template>
  <AppHeader />
  <main class="container pt-4">
    <h1>Boolfolio</h1>
    <ProjectsList :projects="projects" />


  </main>
</template>

<style scoped></style>
