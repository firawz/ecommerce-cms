<template>
  <div>
    <div class="my-3">
      <b-navbar toggleable="lg" type="dark" variant="white">
        <b-img class="my-auto" src="https://www.pngmart.com/files/11/Technology-PNG-Free-Download.png" alt="Left image"
          width="100px"></b-img>
        <b-navbar-brand class="text-dark">UniversalTechnology</b-navbar-brand>
        <b-navbar-toggle target="nav-collapse"></b-navbar-toggle>
        <h1 class="display-5 mx-auto">
          Welcome Admin
        </h1>
        <!-- Right aligned nav items -->
        <b-navbar-nav class="ml-auto">
          <div class="mr-5">
            <button @click.prevent="logout" class="btn btn-outline-danger">
              Logout
            </button>
          </div>
        </b-navbar-nav>
      </b-navbar>
    </div>
    <div>
      <!-- modal -->
      <!-- Button trigger modal -->
      <button type="button" class="btn btn-outline-primary btn-lg mt-5 " data-toggle="modal"
        data-target="#modal1">
        ADD PRODUCT
      </button>
      <!-- Modal -->
      <div class="modal fade" id="modal1" tabindex="-1" role="dialog" aria-labelledby="exampleModalLabel"
        aria-hidden="true">
        <div class="modal-dialog" role="document">
          <div class="modal-content">
            <form @submit.prevent="addProduct" class="p-5">
              <div class="form-group">
                <label>Product Name</label> <br>
                <input v-model="name" type="text" class="form-control"
                  placeholder="Enter The Product Name">
              </div>
              <div class="form-group">
                <label>Image Url</label><br>
                <input v-model="image_url" type="text" class="form-control" placeholder="Image Url">
              </div>
              <div class="form-group">
                <label>Price</label><br>
                <input v-model="price" type="number" class="form-control" placeholder="Price">
              </div>
              <div class="form-group">
                <label>Stock</label><br>
                <input v-model="stock" type="number" class="form-control" placeholder="Stock">
              </div>
              <button type="submit" class="btn btn-outline-success">Submit</button>
            </form>
          </div>
        </div>
      </div>
      <!-- modal -->
    </div>
    <div class="d-sm-flex justify-content-around flex-wrap mx-5 my-5">
      <Cards v-for="product in this.$store.state.data" :key='product.id' :product='product' />
    </div>
    </div>

</template>

<script>
import Cards from '../components/Cards'
import { mapMutations, mapActions } from 'vuex'

export default {
  name: 'Home',
  data () {
    return {
      name: '',
      image_url: '',
      price: 0,
      stock: 0
    }
  },
  components: {
    Cards
  },
  methods: {
    ...mapMutations([
    ]),
    ...mapActions([
      'addProducts'
    ]),
    logout () {
      localStorage.clear()
      this.$router.push('/')
    },
    addProduct () {
      this.addProducts({ name: this.name, image_url: this.image_url, price: this.price, stock: this.stock })
    }
  },

  created () {
    this.$store.dispatch('fetchProducts')
  }
}

</script>

<style scoped>
*{
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.navbar{
  border-bottom-right-radius: 20px;
  border-bottom-left-radius: 20px;
  width: 100vw;
  padding: 0px;
  height: 10vh;
  border-bottom: 4px solid gray;
  color: #004d7b;
  border-color: #004d7b ;
}
</style>
