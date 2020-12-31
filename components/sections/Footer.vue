<template>
  <footer>
    <b-container>
      <b-row align-h="around">
        <b-col md="2" cols="12">
          <img src="~/assets/images/odl-logo.png" class="footerlogo"/>
        </b-col>
        <b-col md="3" sm="6" cols="6" class="footerMenu">
          <navbar mode="footer"></navbar>
        </b-col>
        <b-col md="3" sm="6" cols="6" class="socialLinks">
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

  @media screen and (max-width: 767px) {
    footer {
      height: 100%;
    }

    .footerlogo {
      display: block;
      margin: 20px auto;
    }

    .socialLinks {
      text-align: right;
    }
  }
</style>
