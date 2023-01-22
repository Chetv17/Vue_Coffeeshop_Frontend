<template>
  <div class='container'>
    <h1>Our Menu</h1>
  <ul>
    <li
      v-for="product in products"
      :key="product.id"
    >

    <div class="menuContainer">
      <button class='edit' @dblclick="toggleEdit">
      <img class='menuItem' :src="product.image" />
      <p>{{product.name}} | ${{product.price}}</p>
      <div v-if="toggle"><p class='editbtn'>Edit Menu Item</p>
        <ProductForm
          :productId="product.id"
          :currentName="product.name"
          :currentImage="product.image"
          :currentPrice="product.price" @form-submitted="editProduct"
        />
        <button class='delete' @click="deleteProduct" :value="product.id">Delete</button>
      </div>
    </button>
    </div>
    </li>
  </ul>
  <details><summary>Add Menu Item</summary><ProductForm @form-submitted="createProduct"/>
  </details>
  </div>
</template>
<script>
import ProductForm from '../components/ProductForm'
import axios from 'axios'
export default {
  name: 'HomeView',
  components: {
    ProductForm
  },
  data: function () {
    return {
      products: [],
      toggle: false
    }
  },
  created: function () {
    this.getProducts()
  },
  methods: {
    toggleEdit: function () {
      this.toggle = !this.toggle
    },
    getProducts: function () {
      axios.get(process.env.VUE_APP_API_URL).then(res => {
        console.log(res.data)
        this.products = res.data
      })
    },
    deleteProduct: function (e) {
      axios.delete(`${process.env.VUE_APP_API_URL}/${e.target.value}`).then(() => {
        this.getProducts()
      })
    },
    createProduct: function (productInfo) {
      axios.post(process.env.VUE_APP_API_URL, productInfo).then(res => {
        this.products.push(res.data)
      })
    },
    editProduct: function (updateInfo) {
      axios.put(`${process.env.VUE_APP_API_URL}/${updateInfo.id}`, updateInfo).then(() => {
        this.getProducts()
      })
    }
  }
}
</script>
