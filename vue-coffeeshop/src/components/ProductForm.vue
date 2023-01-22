<template>
    <form @submit.prevent="handleSubmit">
      <input type="text" placeholder="name" v-model="name"/>
      <input type="text" placeholder="image" v-model="image"/>
      <input type="number" placeholder="price" v-model="price"/>
      <input type="submit"/>
    </form>
  </template>

<script>
export default {
  name: 'ProductForm',
  data: function () {
    return {
      name: '',
      image: '',
      price: 0,
      id: null
    }
  },
  props: {
    currentName: String,
    currentImage: String,
    currentPrice: Number,
    productId: Number
  },
  created: function () {
    if (this.currentName) {
      this.name = this.currentName
      this.image = this.currentImage
      this.price = this.currentPrice
      this.id = this.productId
    }
  },
  methods: {
    handleSubmit: function () {
      this.$emit('form-submitted', {
        name: this.name,
        image: this.image,
        price: parseInt(this.price),
        id: this.id
      })
    }
  }
}
</script>
  <style scoped>
    input {
      border-radius: 5px;
      border: 1px solid #ccc;
    }
  </style>
