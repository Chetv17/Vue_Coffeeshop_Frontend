<template>
  <Header />
  <nav>
    <router-link to="/">Home</router-link> |
    <router-link to="/about">About</router-link> |
    <router-link to="/shows">Upcoming Shows</router-link>
  </nav>
  <router-view/>
</template>
<script>
import Header from './components/Header'
export default {
  name: 'App',
  components: {
    Header
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

nav {
  padding: 15px 0 0 0;
  position: absolute;
  left: 15px;
}

nav a {
  font-weight: bold;
  color: #2c3e50;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.delete {
  background: none;
  border: none;
  text-align: center;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  background-color: lightcoral;
  width: 50px;
  height: 30px;
  border-radius: 10px;
  margin-bottom: 10px;
  box-shadow: 1px 1px 1px grey;
}

.edit {
  position: relative;
  left: 48%;
  text-align: center;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  background-color: lightgreen;
  width: 50px;
  height: 20px;
  padding: 5px;
  border-radius: 10px;
  margin-bottom: 10px;
}
li {
  list-style: none;
}

.container {
  text-align: center;
  position: relative;
  top: 100px;
  padding-bottom: 50px;
}

.menuItem {
  width: 300px;
  height: 300px;
  margin-top: 10px;
  border-radius: 10px;
  box-shadow: 1px 1px 1px grey;
}
</style>
