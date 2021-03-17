<template>
<div class="modal carDetailsModal" :id="'carDetailsModal' + carBanana._id" tabindex="-1" role="dialog">
  <div class="modal-dialog" role="document">
    <div class="modal-content">
      <div class="modal-header">
        <h5 class="modal-title">Modal title</h5>
        <button type="button" class="close" data-dismiss="modal" aria-label="Close">
          <span aria-hidden="true">&times;</span>
        </button>
      </div>
      <div class="modal-body">
        <p>Make: {{carBanana.make}}</p>
        <p>Model: {{carBanana.model}}</p>
        <p>Year: {{carBanana.year}}</p>
        <p>Price: {{carBanana.price}}</p>
        <p></p>
        <p>{{testString}}</p>
      </div>
      <div class="modal-footer">
        <button type="button" class="btn btn-danger" @click="deleteCar()">Delort</button>
        <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
      </div>
    </div>
  </div>
</div>
</template>

<script>
import { carsService } from '../services/CarsService'
// import $ from 'jquery'
// NOTE if using npm to install jquery as a library - otherwise make sure script tags are in the index.html

export default {
  name: 'CarDetailsModal',
  props: {
    carBanana: { type: Object, required: true },
    testString: { type: String, required: true }
  },
  setup(props) {
    return {
      async deleteCar() {
        await carsService.deleteCar(props.carBanana._id)
        // eslint-disable-next-line no-undef
        $('#carDetailsModal' + `${props.carBanana._id}`).modal('toggle')
      }
    }
  },
  components: {}
}
</script>

<style lang="scss" scoped>

</style>
