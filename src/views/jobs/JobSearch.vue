<template>
    <h1>Search by Job Title or Type</h1>
    
    <form @submit.prevent="submitted">
        <label>Search by job text 
            <input type="text" v-model.trim="formdata.searchterm">
        </label>
        <button type="submit">
            Submit
        </button>
    </form>

    <h2>Search Results</h2>

    <div v-if="filteredJobs.length">
        <ul>
            <div v-for="job in filteredJobs" :key="job.id" class="job">
                <li><router-link :to="{ name: 'JobDetails', params: { id: job.id } }">
                    {{ job.title }}
                </router-link>
                </li>
            </div>
        </ul>
    </div>
    <div v-else>
        <p>No results</p>
    </div>

</template>

<script>
export default {
    data() {
        return {
            jobs: [],
            filteredJobs: [],
            formdata: {
                searchterm: ""
            }
        }
    },
    mounted() {
        fetch("http://localhost:3000/jobs")
            .then(response => response.json())
            .then(data => this.jobs = data)
            .catch(err => console.log(err.message))
    },
    methods: {
        submitted: function () {
            this.filteredJobs = this.jobs.filter((job) => job.title.includes(this.formdata.searchterm))
        }
    }
}
</script>

