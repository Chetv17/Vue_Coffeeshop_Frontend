<template>
    <form @submit.prevent="handleShowSubmit">
      <input type="text" placeholder="event" v-model="event"/>
      <input type="text" placeholder="date" v-model="date"/>
      <input type="number" placeholder="price" v-model="price"/>
      <input type="submit"/>
    </form>
  </template>

<script>
export default {
  name: 'ShowForm',
  data: function () {
    return {
      event: '',
      date: '',
      price: 0,
      id: null
    }
  },
  props: {
    currentEvent: String,
    currentDate: String,
    currentPrice: Number,
    showId: Number
  },
  created: function () {
    if (this.currentEvent) {
      this.event = this.currentEvent
      this.date = this.currentDate
      this.price = this.currentPrice
      this.id = this.showId
    }
  },
  methods: {
    handleShowSubmit: function () {
      this.$emit('form-submitted', {
        event: this.event,
        date: this.date,
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
