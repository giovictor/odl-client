<template>
  <nav class="navbar" :class="[ mode == 'header' ? 'headerNav' : 'footerNav']">
    <a href="#" class="link" :class="[ mode == 'header' ? 'headerLink' : 'footerLink']" v-for="(section, index) in sections" :key="index" v-scroll-to="section.path">{{section.name}}</a>
  </nav>
</template>

<script>
export default {
  name: 'Navbar',
  props: {
    mode: { type: String, required: true },
  },
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

  .headerNav {
    flex-direction: row;
  }

  .footerNav {
    flex-direction: column;
    align-items: start;
  }

  .link {
    text-transform: uppercase;
    font-weight: 600;
    letter-spacing: 0.12em;
  }

  .headerLink {
    color: #171717;
    font-size: 13px;
  }

  .footerLink {
    color: #ffffff;
    margin-bottom: 10px;
    font-size: 15px;
  }

  .headerLink:hover {
    color: #171717;
  }

  .footerLink:hover {
    color: #ffffff;
  }

  @media screen and (max-width: 575px) {
    .headerLink {
      font-size: 12px;
    }
  }
</style>
