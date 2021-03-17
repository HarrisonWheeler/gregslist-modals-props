<template>
  <div class="col-4">
    <!-- NOTE the route contains both the name and an object to provide needed params -->
      <div class="card car">
        <img class="card-img-top" :src="car.imgUrl" alt="car">
        <div class="card-body">
          <h4 class="card-title">{{car.make}} | {{car.model}}</h4>
          <p class="card-text">{{car.year}} | {{car.price}}</p>
        </div>
      </div>
        <button class="btn btn-primary" data-toggle="modal" :data-target="'#carDetailsModal' + car._id">Car Deetz</button>
      <CarDetailsModal :carBanana="car" :testString="'hi isabelle!'" />
      <!-- you can pass multiple props if needed -->
      <!-- left as carBanana to demonstrate that the prop name just needs to be consistent in the parent and child -->
  </div>
</template>

<script>
import CarDetailsModal from '../components/CarDetailsModal'

export default {
  name: 'car',
  props: {
    car: Object
  },
  setup() {
    return {}
  },
  components: {
    CarDetailsModal
  }
}
</script>

<style scoped>
.car:hover {
  transform: translateY(-5px);
  box-shadow: 1px 3px 5px rgb(94, 94, 94);
  cursor: pointer
}

.car {
  transition: all .2s;
  color: black
}
</style>
