<template>
    <div v-if="job">
        <h1>Job Detail Page</h1>
        <p>the job id is {{ id }}</p>
        <p>{{ job?.title }}</p>
        <p>{{ job?.details }}</p>
    </div>
    <div v-else>
        <p>
            Loading data....
        </p>
    </div>
</template>

<script>
export default {
    props: ['id'],
    data() {
        return {
            job: null
        };
    },
    mounted() {
        fetch("http://127.0.0.1:8000/api/job/" + this.id)
            .then(response => response.json())
            .then(data => {
                this.job = data.job;
            })
            .catch(err => console.log(err.message));
    }
}
</script>

<style></style>