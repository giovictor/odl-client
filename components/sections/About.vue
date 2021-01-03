<template>
  <div id="about">
    <div class="backgroundObjects">
      <background-object id="fruits-and-veggies-1" :src="require(`~/assets/images/fruits-and-veggies-1.png`)" bottom="0" left="0"></background-object>
      <background-object id="fruits-and-veggies-2" :src="require(`~/assets/images/fruits-and-veggies-2.png`)" top="0" right="0"></background-object>
      <background-object id="veggie-bowl-2" :src="require(`~/assets/images/veggie-bowl-2.png`)" bottom="35px" right="52px"></background-object>
      <background-object id="cherry-about" :src="require(`~/assets/images/cherry.png`)" top="0" right="0"></background-object>
      <background-object id="strawberry-about" :src="require(`~/assets/images/strawberry.png`)" bottom="0" left="-20px"></background-object>
    </div>
    <b-container>
      <b-row align-v="center" align-h="center">
        <b-col cols="9">
          <h2>About Us</h2>
          <section>
            <h3>Our brief history</h3>
            <p>Orlando’s Des Legumes is named after our father. "Des Legumes" is a french word that means "Vegetables" that we combined it next to our father’s name.</p>
          </section>
          <section>
            <h3>Who we are & what we do</h3>
            <p>We are from Apolonio’s family and we are a vegetable supplier from the roots of Northern Samar and was given the opportunity to be part of the Province of Benguet. We are farmers traders and became a restaurant supplier of vegetables, fruits, eggs, and rice.</p>
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

  #strawberry-about, #cherry-about {
    display: none;
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

  @media screen and (max-width: 1330px) {
    #veggie-bowl-2 {
      display: none;
    }
  }

  @media screen and (max-width: 1199px) {
    #fruits-and-veggies-1 {
      left: -10px !important;
    }

    #fruits-and-veggies-2 {
      top: -25px !important;
    }
  }

  @media screen and (max-width: 991px) {
    #about h2 {
      font-size: 22px;
    }

    #about h3 {
      font-size: 18px;
    }

    #about p {
      font-size: 14px;
    }
  }

  @media screen and (max-width: 767px) {
    #fruits-and-veggies-1,  #fruits-and-veggies-2 {
      display: none;
    }

    #strawberry-about, #cherry-about {
      display: block;
    }

    #about h3 {
      color: #f6961e;
    }
  }

  @media screen and (max-width: 575px) {
    #about {
      height: 100%;
      padding-bottom: 84px;
    }
  }
</style>
