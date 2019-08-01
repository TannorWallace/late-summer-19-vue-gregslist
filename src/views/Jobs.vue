<template>
  <div class="jobs container">
    <h1>Fuggin Jerbs</h1>
    <div class="row">

      <div class=" col-4 border border-dark" v-for="job in jobs" @click="viewJob(job)">
        <h5>Job Title:{{job.jobTitle}}</h5>
        <p>Company:{{job.company}}</p>
        <p>Hours:{{job.hours}}</p>
        <p>Rate:{{job.rate}}</p>
        <p>Job Description:{{job.description}}</p>
        <button class="btn btn-warning rounded mb-1 border border-dark">Apply</button>
      </div>
    </div>
  </div>
</template>


<script>
  export default {
    name: 'jobs',
    data() {
      return {
        newJob: {}
      }
    },
    mounted() {
      this.$store.dispatch('getJobs')
    },
    computed: {
      jobs() {
        return this.$store.state.jobs
      }
    },
    methods: {
      viewJob(job) {
        this.$router.push({ name: 'job', params: { jobId: job._id } })
      },
      addJob() {
        this.$store.dispatch('addJob', this.newJob)
      }
    },
    components: {}
  }
</script>


<style scoped>
  h5 {
    text-decoration: underline;
  }
</style>