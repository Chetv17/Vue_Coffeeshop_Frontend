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
  top: 50px;
  left: 15px;
}

nav a {
  font-weight: bold;
  color: ivory;
}

nav a.router-link-exact-active {
  color: #42b983;
}

.delete {
  position: relative;
  background: none;
  border: none;
  text-align: center;
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  background-color: lightcoral;
  width: 25%;
  height: 30px;
  border-radius: 10px;
  margin-top: 20px;
  margin-bottom: 10px;
  box-shadow: 1px 1px 1px grey;
}

.edit {
  background: none;
  border: none;
  margin-bottom: 10px;
  cursor: pointer;
}

.editbtn {
  font-family: Impact, Haettenschweiler, 'Arial Narrow Bold', sans-serif;
  font-size: 20px;
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

.header {
  margin-top: 0;
  margin-bottom: 45px;
  padding-left: 5px;
}
</style>
