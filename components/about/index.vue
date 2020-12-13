<template>
  <div id="about">
    <div class="backgroundObjects">
      <background-object :src="require(`~/assets/images/fruits-and-veggies-1.png`)" bottom="0" left="0"></background-object>
      <background-object :src="require(`~/assets/images/fruits-and-veggies-2.png`)" top="0" right="0"></background-object>
      <background-object :src="require(`~/assets/images/veggie-bowl-2.png`)" bottom="35px" right="52px"></background-object>
    </div>
    <b-container>
      <b-row align-v="center" align-h="center">
        <b-col cols="9">
          <h2>About Us</h2>
          <section>
            <h3>Our brief history</h3>
            <p>Orlando’s Des Legumes was named after our father. “Des Legumes” was a french word which means “Vegetables” so that we decided to combined it next to our father’s name.</p>
          </section>
          <section>
            <h3>Who we are & what we do</h3>
            <p>We are from Apolonio’s family and we are a vegetable supplier from the roots of Northern Samar and was given an opportunity to be part of Province of Benguet. We are farmers traders and became a restaurant supplier of vegetables, eggs and rice.</p>
          </section>
        </b-col>
      </b-row>
    </b-container>
  </div>
</template>

<script>
import BackgroundObject from '@/components/component/backgroundObject'

export default {
  name: 'About',
  components: {
    BackgroundObject
  }
}
</script>

<style>
  #about {
    width: 100%;
    height: 600px;
    position: relative;
    padding-top: 84px;
  }

  #about section {
    margin-top: 63px;
  }

  #about h2, #about h3 {
    text-transform: uppercase;
  }

  #about h2 {
    font-weight: 700;
    font-size: 24px;
    color: #89b83e;
    letter-spacing: 0.2em;
  }

  #about h3 {
    font-weight: 800;
    font-size: 20px;
    color: #050505;
    letter-spacing: 0.12em;;
  }

  #about p {
    font-size: 16px;
    font-weight: 400;
    letter-spacing: 0.05em;
    text-align: justify;
    line-height: 1.5em;
  }
</style>
