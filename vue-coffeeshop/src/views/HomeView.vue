<template>
  <div class='container'>
    <h1>Menu</h1>
  <ul>
    <li
      v-for="product in products"
      :key="product.id"
    >
      <img class='menuItem' :src="product.image" />
      <p>{{product.name}}</p>
      <p>${{product.price}}</p>

      <button class='delete' @click="deleteProduct" :value="product.id">Delete</button>

      <details><summary class="edit">Edit</summary>
        <ProductForm
          :productId="product.id"
          :currentName="product.name"
          :currentImage="product.image"
          :currentPrice="product.price" @form-submitted="editProduct"
        />
      </details>

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
      products: []
    }
  },
  created: function () {
    this.getProducts()
  },
  methods: {
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
