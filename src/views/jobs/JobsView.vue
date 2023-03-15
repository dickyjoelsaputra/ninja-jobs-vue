<template>
    <div v-if="jobs.length">
        <h1>Jobs</h1>
        <div v-for="job in jobs" :key="job.id">
            <router-link :to="{ name: 'job-details', params: { id: job.id } }">
                <h2>{{ job.title }}</h2>
            </router-link>
        </div>
    </div>
    <div v-else>
        <p>
            Loading data....
        </p>
    </div>
</template>

<script>
export default {
    data() {
        return {
            jobs: []
        };
    },
    mounted() {
        fetch("http://127.0.0.1:8000/api/jobs")
            .then(response => response.json())
            .then(data => {
                this.jobs = data.jobs;
            });
    }
};
</script>

<style></style>