<script>
export default {
    name: 'ProjectCard',
    props: { project: Object, isDetail: Boolean },
    computed: {
        abstract() {
            const abstract = this.project.content.slice(0, 550);
            return abstract + '...';
        },

        pubblicationDate() {
            const date = new Date(this.project.created_at);

            let day = date.getDate();
            let month = date.getMonth() + 1;
            const year = date.getFullYear();
            const hours = date.getHours();
            const minutes = date.getMinutes();

            if (day < 10) day = '0' + day;
            if (month < 10) month = '0' + month;


            return `${day}/${month}/${year} alle ${hours}:${minutes}`
        }
    }
};
</script>

<template>
    <div class="card my-5">
        <div class="card-header d-flex align-items-center justify-content-between">
            <h2>{{ project.title }}</h2>
            <RouterLink v-if="!isDetail" class="btn btn-sm btn-primary"
                :to="{ name: 'project-detail', params: { slug: project.slug } }">Vedi
            </RouterLink>
            <RouterLink v-else="showHomeLink" class="btn btn-sm btn-primary" :to="{ name: 'home' }">Home</RouterLink>
        </div>
        <div class="card-body">
            <span v-if="project.type" class="badge mb-2" :style="{ backgroundColor: project.type.color }">{{
                project.type.label }}</span>
            <p>{{ isDetail ? project.content : abstract }}</p>

            <div v-if="project.technologies.length" class="d-flex justify-content-end">
                <span v-for="technology in project.technologies" :key="technology.id" class="badge rounded-pill me-2"
                    :class="`text-bg-${technology.color}`"> {{ technology.label }}
                </span>
            </div>
        </div>
        <div class="card-footer d-flex justify-content-end">
            <small>Pubblicato il {{ pubblicationDate }}</small>
        </div>
    </div>
</template>


<style></style>