<template>
  <nav class="navbar">
    <a href="#" class="link" v-for="(section, index) in sections" :key="index" v-scroll-to="section.path">{{section.name}}</a>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  data() {
    return {
      sections: [
        {
          path: "#home",
          name: "Home"
        },
        {
          path: "#about",
          name: "About"
        },
        {
          path: "#gallery",
          name: "Gallery"
        },
        {
          path: "#contact",
          name: "Contact"
        }
      ]
    }
  }
}
</script>

<style>
  .navbar {
    display: flex;
    justify-content: space-evenly;
  }

  .link {
    text-transform: uppercase;
    font-size: 13px;
    font-weight: 600;
    color: #171717;
    letter-spacing: 0.12em;
  }

  .link:hover {
    color: #171717;
  }
</style>
