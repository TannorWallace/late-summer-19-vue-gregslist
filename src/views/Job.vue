<template>
  <div class="job">
    <div class="col-4 border border-dark" v-for="job in jobs">
      <h5>Job Title:{{job.jobTitle}}</h5>
      <p>Company:{{job.company}}</p>
      <p>Hours:{{job.hours}}</p>
      <p>Rate:{{job.rate}}</p>
      <p>Job Description:{{job.description}}</p>
      <button class="btn btn-danger border border-dark" @click="deleteJob">Delete</button>
    </div>

  </div>
</template>


<script>
  export default {
    name: 'job',
    data() {
      return {}
    },
    mounted() {
      let dataToSend = {
        jobId: this.$route.params.jobId
      }
      this.$store.dispatch('getJobById', dataToSend)
    },
    computed: {
      job() {
        return this.$store.state.activeJob
      }
    },
    methods: {
      deleteJob() {
        this.$store.dispatch('deleteJob', this.job._id)
      }
    },
    components: {}
  }
</script>


<style scoped>

</style>