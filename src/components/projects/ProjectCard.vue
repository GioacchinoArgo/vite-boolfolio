<script>
export default {
    name: 'ProjectCard',
    props: { project: Object },
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
        <div class="card-header">
            <h2>{{ project.title }}</h2>
        </div>
        <div class="card-body">
            <p>{{ abstract }}</p>
        </div>
        <div class="card-footer d-flex justify-content-between">
            <address>By: {{ project.id }}</address>
            <small>Pubblicato il {{ pubblicationDate }}</small>
        </div>
    </div>
</template>


<style></style>