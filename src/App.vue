<template>
  <div id="main-div" class="main color">
    <Navbar />
    <Profile />
    <Projects />
    <Contact />
  </div>
</template>

<script>
import Navbar from './components/Navbar.vue';
import Profile from './components/Profile.vue';
import Projects from './components/Projects.vue';
import Contact from './components/Contact.vue';
  export default {
    name: "App",
    components: {
      Navbar,
      Profile,
      Projects,
      Contact,
    },
    setup() {
    }
  }
</script>

<style scoped>
.main {
  padding: 0; 
  margin: 0;
  display: block;
  position: relative;
}
.color {
  background-color: var(--main-color);
  color: var(--text-color);
}
.dark {
  --main-color: var(--dark-main-color);
  --text-color: var(--dark-text-color);
}

</style>