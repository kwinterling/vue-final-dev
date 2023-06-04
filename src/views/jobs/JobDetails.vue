<template>
    
    <div v-if="job">
        <h1>{{ job.title }}</h1>
        
        <p>The job id is {{ this.$route.params.id }}</p>
        <p>{{ job.details }}</p>
        <p>The type of job is {{ jobType }}</p>
    </div>
    <div v-else>
        <p>Loading job details...</p>
    </div>
</template>

<script>
export default {
    props: ['id'],
    computed: {
        jobType: function() {
            let jType = "";

            if (this.job.title.includes("Developer")) {
                jType = "Software development";
            } else if (this.job.title.includes("Accountant")) {
                jType = "Financial";
            } else {
                jType = "Unknown";
            }

            return jType;
        }
    },
    data() {
        return {
            job: null
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs/' + this.$route.params.id)
            .then(response => response.json())
            .then(data => this.job = data)
            .catch(err => err.message)
    }
}
</script>

<style>
</style>
