<template>
  <div>
      <div class="mx-lg-5 my-lg-5">
        <b-card :title="product.name" :img-src="product.image_url" img-alt="Image" img-top
          tag="article" style="max-width: 20rem;" class="mb-2">
          <b-card-text> <br>
            Price: <br>
            Rp.{{product.price}}
          </b-card-text>
          <br>
            STOCK : {{product.stock}}
            <br>
            <br>
            <div class="row mx-auto justify-content-around">
          <b-button size="md" class="rounded-pill" variant="outline-success">Update</b-button>
          <b-button @click.prevent='deleteProduct(product.id)' class="rounded-pill" variant="outline-danger">Delete</b-button>
            </div>
        </b-card>
      </div>
    </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
  name: 'Cards',
  props: ['product'],
  methods: {
    ...mapActions([
      'deleteProducts'
    ]),
    deleteProduct (id) {
      this.deleteProducts(id)
    }
  }
}
</script>

<style>

</style>
