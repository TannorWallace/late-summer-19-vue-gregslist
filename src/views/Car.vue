<template>
  <div class="car">
    <h5>{{car.make}}</h5>
    <img :src="car.imgUrl" alt="">
    <p>{{car.model}}</p>
    <p>{{car.year}}</p>
    <p>{{car.price}}</p>
    <button class="btn btn-danger" @click="deleteCar">Delete</button>
  </div>
</template>


<script>
  export default {
    name: 'car',
    data() {
      return {}
    },
    mounted() {
      let dataToSend = {
        carId: this.$route.params.carId,
        otherId: "1sadaskjhasjh3223432"
      }
      // if we need to pass more than one argument, we build a payload object to send "dataToSend"
      this.$store.dispatch('getCarById', dataToSend)
    },
    computed: {
      car() {
        return this.$store.state.activeCar
      }
    },
    methods: {
      deleteCar() {
        this.$store.dispatch('deleteCar', this.car._id)
      }
    },
    components: {}
  }
</script>


<style scoped>

</style>