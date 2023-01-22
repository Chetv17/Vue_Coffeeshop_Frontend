<template>
  <div class='container'>
    <h1>Upcoming Shows</h1>
  <ul>
    <li
      v-for="show in shows"
      :key="show.id"
    >

    <div class="menuContainer">
      <button class='edit' @dblclick="toggleEdit">
      <p>{{show.event}} | {{show.date}} | Admission: ${{show.price}}</p>
      <div v-if="toggle"><p class='editbtn'>Edit Show Info</p>
        <ShowForm
          :showId="show.id"
          :currentEvent="show.event"
          :currentDate="show.date"
          :currentPrice="show.price" @form-submitted="editShow"
        />
        <button class='delete' @dblclick="deleteShow" :value="show.id">Delete</button>
      </div>
    </button>
    </div>
    </li>
  </ul>
  <details><summary>Add A New Event</summary><ShowForm @form-submitted="createShow"/>
  </details>
  </div>
</template>
<script>
import ShowForm from '../components/ShowForm'
import axios from 'axios'
export default {
  name: 'ShowView',
  components: {
    ShowForm
  },
  data: function () {
    return {
      shows: [],
      toggle: false
    }
  },
  created: function () {
    this.getShows()
  },
  methods: {
    toggleEdit: function () {
      this.toggle = !this.toggle
    },
    getShows: function () {
      axios.get(process.env.VUE_APP_API_URL_TWO).then(res => {
        console.log(res.data)
        this.shows = res.data
      })
    },
    deleteShow: function (e) {
      axios.delete(`${process.env.VUE_APP_API_URL_TWO}/${e.target.value}`).then(() => {
        this.getShows()
      })
    },
    createShow: function (showInfo) {
      axios.post(process.env.VUE_APP_API_URL_TWO, showInfo).then(res => {
        this.shows.push(res.data)
      })
    },
    editShow: function (updateInfo) {
      axios.put(`${process.env.VUE_APP_API_URL_TWO}/${updateInfo.id}`, updateInfo).then(() => {
        this.getShows()
      })
    }
  }
}
</script>
