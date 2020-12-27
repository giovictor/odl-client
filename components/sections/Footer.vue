<template>
  <footer>
    <b-container>
      <b-row align-h="around">
        <b-col cols="2">
          <img src="~/assets/images/odl-logo.png" class="footerlogo"/>
        </b-col>
        <b-col cols="3">
          <navbar mode="footer"></navbar>
        </b-col>
        <b-col cols="3">
          <p>Follow Us On:</p>
          <a href="https://www.facebook.com/orlandosveggies" target="_blank" class="h2 mr-1 socialLink"><b-icon icon="facebook"></b-icon></a>
          <a href="https://www.instagram.com/orlandosdeslegumes" target="_blank" class="h2 mr-1 socialLink"><b-icon icon="instagram"></b-icon></a>
        </b-col>
      </b-row>
    </b-container>
  </footer>
</template>

<script>
import Navbar from '@/components/component/navbar'
import { BIcon, BIconFacebook, BIconInstagram } from 'bootstrap-vue'

export default {
  name: 'Footer',
  components: {
    Navbar,
    BIcon,
    BIconFacebook,
    BIconInstagram
  }
}
</script>

<style>
  footer {
    background-color: #1e1c1c;
    color: #ffffff;
    width: 100%;
    height: 254px;
    display: flex;
    align-items: center;
    font-size: 15px;
    text-transform: uppercase;
    font-weight: 700;
  }

  .footerlogo {
    width: 122px;
    height: 123px;
  }

  .socialLink {
    color: #ffffff;
    transition: all 0.3s ease-in-out;
  }

  .socialLink:hover {
    color: #343a40;
  }
</style>
