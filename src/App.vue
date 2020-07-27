<template>
  <div id="app">
    <v-app>
      <NavBar></NavBar>
      <Jumbotron></Jumbotron>
      <router-view />
      <center><Footer></Footer></center>
    </v-app>
  </div>
</template>

<script>
import NavBar from './components/shared/NavBar'
import Footer from './components/shared/Footer'
import Jumbotron from './components/shared/Jumbotron'
export default {
  name: "App",
  methods: {
    Logout() {
      this.$root.store.logout();
      this.$root.toast("Logout", "User logged out successfully", "success");

      this.$router.push("/").catch(() => {
        this.$forceUpdate();
      });
    }
  },
  components: {
    NavBar,
    Footer,
    Jumbotron
  },
};

</script>

<style lang="scss">
@import "@/scss/form-style.scss";

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  min-height: 100vh;
}

#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
</style>
