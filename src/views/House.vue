<template>
  <div class="house">
    <img :src="house.imgUrl" alt="">
    <h5>Price:${{house.price}}</h5>
    <p>Bedrooms:{{house.bedrooms}}</p>
    <p>Bathrooms:{{house.bathrooms}}</p>
    <p>Levels:{{house.levels}}</p>
    <p>Year Built: {{house.year}}</p>
    <button class="btn btn-warning" @click="deleteHouse">Explode!</button>
  </div>

</template>


<script>
  export default {
    name: 'house',
    data() {
      return {}
    },
    mounted() {
      let dataToSend = {
        houseId: this.$route.params.houseId,
      }
      this.$store.dispatch('getHouseById', dataToSend)
    },
    computed: {
      house() {
        return this.$store.state.activeHouse
      }
    },
    methods: {
      deleteHouse() {
        this.$store.dispatch('deleteHouse', this.house._id)
      }
    },
    components: {}
  }
</script>


<style scoped>
  img {
    height: 300px;
    width: 300px;
  }
</style>