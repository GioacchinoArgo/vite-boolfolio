<script>
import ProjectsList from '../components/projects/ProjectsList.vue';
import axios from 'axios';
const endpoint = 'http://localhost:8000/api/projects/';

export default {
    name: 'HomePage',
    components: { ProjectsList },
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

    <h1>Boolfolio</h1>
    <ProjectsList :projects="projects" />

</template>

<style scoped></style>
