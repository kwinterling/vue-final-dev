<template>
    <h1>Jobs</h1>

    <div v-if="jobs.length">
        <ul>
        <div v-for="job in jobs" :key="job.id" class="job">
            <router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
                <li>{{ job.title }}</li>
            </router-link>
        </div>
        </ul>
    </div>
    <div v-else>
        <p>Loading jobs...</p>
    </div>
</template>

<script>
import axios from 'axios';


export default {
    data() {
        return {
            jobs: []
        }
    },
    mounted() {
        fetch('http://localhost:3000/jobs')
            .then(response => response.json())
            .then(data => this.jobs = data)
            .catch(err => console.log(err.message))
    }
}
</script>