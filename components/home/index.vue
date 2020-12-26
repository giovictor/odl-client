<template>
  <div id="home">
    <div class="backgroundObjects">
      <background-object :src="require(`~/assets/images/strawberry.png`)" top="187px" left="-20px"></background-object>
      <background-object :src="require(`~/assets/images/celery.png`)" top="0" left="504px"></background-object>
      <background-object :src="require(`~/assets/images/cherry.png`)" top="45px" right="0"></background-object>
      <background-object :src="require(`~/assets/images/herb.png`)" bottom="0" left="329px"></background-object>
      <background-object :src="require(`~/assets/images/broccoli.png`)" bottom="54px" right="0"></background-object>
    </div>
    <header>
      <b-container>
        <b-row align-v="center" align-h="center">
          <b-col cols="4">
            <img src="~/assets/images/logo.png"/>
          </b-col>
          <b-col cols="4">
            <navbar></navbar>
          </b-col>
        </b-row>
      </b-container>
    </header>
    <section>
      <b-container>
        <b-row align-v="center" align-h="center">
          <b-col cols="5">
            <div class="quote">
              <img id="upper-leaf-quote" src="~/assets/images/upper-leaf-quote.png"/>
              <p>Fitter</p>
              <p>Healthier</p>
              <p>Happier.</p>
              <img id="lower-leaf-quote" src="~/assets/images/lower-leaf-quote.png"/>
            </div>
            <div class="description">
              <p>Get healthier in your everyday life.</p>
            </div>
            <b-button pill class="cta" href="#" size="lg" v-scroll-to="'#contact'">Get In Touch</b-button>
          </b-col>
          <b-col cols="4">
            <img src="~/assets/images/veggie-bowl.png"/>
          </b-col>
        </b-row>
      </b-container>
    </section>
  </div>
</template>

<script>
import BackgroundObject from '@/components/component/backgroundObject'
import Navbar from '@/components/home/navbar'

export default {
  name: 'Home',
  components: {
    BackgroundObject,
    Navbar
  }
}
</script>

<style>
  #home {
    width: 100%;
    height: 600px;
    position: relative;
  }

  #home header {
    padding-top: 33px;
  }

  #home section, .description, .cta {
    margin-top: 15px;
  }

  .quote {
    font-size: 50px;
    text-transform: uppercase;
    position: relative;
  }

  .quote p {
    margin: 0;
    font-family: 'Gretaros';
  }

  .quote p:nth-of-type(1), .quote p:nth-of-type(2) {
    color: #89b83e;
  }

  .quote p:nth-of-type(3) {
    color: #f6961e;
  }

  #upper-leaf-quote {
    position: absolute;
    left: -34px;
    top: -14px;
  }

  #lower-leaf-quote {
    position: absolute;
    top: 140px;
    left: 242px;
  }

  .description p {
    color: #362f2d;
    font-size: 14px;
    font-weight: 600;
  }

  .cta {
    text-transform: uppercase;
    background-color: #f6961e;
    border-color: #f6961e;
    font-size: 15px;
    letter-spacing: 0.24em;
    font-weight:700;
    padding: 10px 20px;
  }

  .cta:hover {
    background-color: #89b83e;
    border-color: #89b83e;
  }
</style>
