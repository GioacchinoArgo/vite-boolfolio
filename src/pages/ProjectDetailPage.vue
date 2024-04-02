<script>
import axios from 'axios';
import ProjectCard from '../components/projects/ProjectCard.vue';
const endpoint = 'http://localhost:8000/api/projects/';
export default {
    name: 'ProjectDetailPage',
    components: { ProjectCard },
    data: () => ({
        project: null,
    }),
    methods: {
        getProject() {
            axios.get(endpoint + this.$route.params.slug)
                .then(res => {
                    this.project = res.data;
                })
                .catch(err => { console.error(err) })
                .then()
        }
    },
    created() {
        this.getProject();
    }
};
</script>

<template>
    <ProjectCard v-if="project" :project="project" :isDetail="true" />
</template>

<style></style>