<template>
  <div class="houses container-fluid">
    <h1>Mofoin' Houses!</h1>
    <div class="row justify-content-center">
      <form class="col-8 pb-5" @submit.prevent="addHouse">
        <div class="form-group">
          <label for="price">Price</label>
          <input type="number" name="make" class="form-control" id="price" min="0" placeholder="Enter Price"
            v-model="newHouse.price">
        </div>
        <div class="form-group">
          <label for="bedrooms">Bedrooms</label>
          <input type="number" name="Bedrooms" class="form-control" id="bedrooms" min="0" placeholder="Enter Bedrooms"
            v-model="newHouse.bedrooms">
        </div>
        <div class="form-group">
          <label for="bathrooms">Bathrooms</label>
          <input type="number" name="bathrooms" class="form-control" id="bathrooms" min="0"
            placeholder="Enter Bathrooms" v-model="newHouse.bathrooms">
        </div>

        <div class="form-group">
          <label for="img">Image</label>
          <input type="text" class="form-control" id="img" placeholder="Enter image url" v-model="newHouse.imgUrl">
        </div>

        <div class="form-group">
          <label for="levels">Levels</label>
          <input type="number" class="form-control" placeholder="Enter Levels" min="1" max="5" id="levels"
            v-model="newHouse.levels">
        </div>

        <div class="form-group">
          <label for="year">Year</label>
          <input type="number" class="form-control" placeholder="Year Built" min="1900" id="year"
            v-model="newHouse.year">
        </div>


        <button type="submit" class="btn btn-block btn-success border border-dark">Submit</button>
      </form>
    </div>

    <div class="row">
      <div class="col-4 border border-dark p-1" v-for="house in houses" @click="viewHouse(house)">
        <img :src=" house.imgUrl" alt="">
        <h5>Price:${{house.price}}</h5>
        <p>Bedrooms:{{house.bedrooms}}</p>
        <p>Bathrooms:{{house.bathrooms}}</p>
        <p>Levels:{{house.levels}}</p>
        <p>Year Built: {{house.year}}</p>
      </div>
    </div>
  </div>
</template>


<script>
  export default {
    name: 'houses',
    data() {
      return {
        newHouse: {}
      }
    },

    mounted() {
      this.$store.dispatch('getHouses')
    },

    computed: {
      // this references the collection on our store's state
      houses() {
        return this.$store.state.houses

      }
    },
    methods: {
      viewHouse(house) {
        this.$router.push({ name: 'house', params: { houseId: house._id } })
      },
      addHouse() {
        this.$store.dispatch('addHouse', this.newHouse)
      },
    },
    components: {}
  }
</script>


<style scoped>
  img {
    height: 300px;
    width: 300px;
  }

  form .form-control {
    border: solid 2px black;
  }


  .des {
    border: solid 2px black;

  }
</style>