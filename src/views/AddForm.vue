<template>
  <div>
    <Navbar class="mb-3"></Navbar>
    <h3 class="text-center">Add a new product</h3>
    <div class="container my-5 py-3 border border-dark rounded bg-secondary text-white" style="width: 40%;">
        <div class="container">
            <form id="addForm" v-on:submit.prevent="addProduct">
                <div class="form-group">
                    <label for="name">Name</label>
                    <input type="text" class="form-control" v-model="name">
                </div>
                <div class="form-group">
                    <label for="image_url">Image URL</label>
                    <textarea class="form-control" rows="1" v-model="image_url"></textarea>
                </div>
                <div class="form-group">
                    <label for="category">Category</label>
                    <input type="text" class="form-control" v-model="category">
                </div>
                <div class="form-group">
                    <label for="price">Price</label>
                    <input type="number" class="form-control" name="price" v-model="price">
                </div>
                <div class="form-group">
                    <label for="stock">Stock(s)</label>
                    <input type="number" class="form-control" v-model="stock">
                </div>
                <button type="submit" class="btn btn-primary" style="width: 100%;">Add</button>
                <button type="button" class="btn btn-danger my-2" style="width: 100%;" v-on:click.prevent="home">Cancel</button>
            </form>
        </div>
    </div>
</div>
</template>

<script>
import Navbar from '../components/Navbar'
export default {
  name: 'AddForm',
  components: {
    Navbar
  },
  data () {
    return {
      name: '',
      image_url: '',
      price: '',
      stock: '',
      category: ''
    }
  },
  methods: {
    home () {
      this.$router.push({ name: 'Home' })
    },
    addProduct () {
      const product = {
        name: this.name,
        image_url: this.image_url,
        price: this.price,
        stock: this.stock,
        category: this.category
      }
      this.$store.dispatch('addProduct', product)
    }
  }
}
</script>

<style>

</style>
