<template>
  <div id="home">
    <div class="backgroundObjects">
      <background-object id="strawberry" :src="require(`~/assets/images/strawberry.png`)" top="187px" left="-20px"></background-object>
      <background-object id="celery" :src="require(`~/assets/images/celery.png`)" top="0" left="37%"></background-object>
      <background-object id="cherry" :src="require(`~/assets/images/cherry.png`)" top="45px" right="0"></background-object>
      <background-object id="herb" :src="require(`~/assets/images/herb.png`)" bottom="0" left="24%"></background-object>
      <background-object id="broccoli" :src="require(`~/assets/images/broccoli.png`)" bottom="54px" right="0"></background-object>
    </div>
    <header>
      <b-container>
        <b-row align-v="center" align-h="center">
          <b-col lg="4" md="3">
            <img src="~/assets/images/odl-logo.png" class="headerlogo"/>
          </b-col>
          <b-col lg="5" md="6">
            <navbar mode="header"></navbar>
          </b-col>
        </b-row>
      </b-container>
    </header>
    <section>
      <b-container>
        <b-row align-v="center" align-h="center">
          <b-col md="5" cols="12">
            <div class="quote">
              <p><img id="upper-leaf-quote" src="~/assets/images/upper-leaf-quote.png"/>Fitter</p>
              <p>Healthier</p>
              <p>Happier.<img id="lower-leaf-quote" src="~/assets/images/lower-leaf-quote.png"/></p>
            </div>
            <div class="description">
              <p>Get healthier in your everyday life.</p>
            </div>
            <div class="ctaButtons">
              <b-button pill class="cta getintouch" href="#" size="lg" v-scroll-to="'#contact'">Get In Touch</b-button>
              <b-button pill class="cta ordernow" href="#" size="lg">Order Now</b-button>
            </div>
          </b-col>
          <b-col md="4" class="veggie-bowl">
            <img src="~/assets/images/veggie-bowl.png"/>
          </b-col>
        </b-row>
      </b-container>
    </section>
  </div>
</template>

<script>
import BackgroundObject from '@/components/component/backgroundObject'
import Navbar from '@/components/component/navbar'

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

  .headerlogo {
    width: 77px;
    height: 78px;
  }

  .quote {
    font-size: 50px;
    text-transform: uppercase;
  }

  .quote p {
    margin: 0;
    font-family: 'Gretaros';
    position: relative;
  }

  .quote p:nth-of-type(1), .quote p:nth-of-type(2) {
    color: #89b83e;
  }

  .quote p:nth-of-type(3) {
    color: #f6961e;
  }

  #upper-leaf-quote {
    position: absolute;
    top: -15px;
    left: -33px;
  }

  #lower-leaf-quote {
    position: absolute;
    left: 242px;
    top: 0px;
  }

  .description p {
    color: #362f2d;
    font-size: 14px;
    font-weight: 600;
  }

  .cta {
    text-transform: uppercase;
    font-size: 15px;
    letter-spacing: 0.24em;
    font-weight:700;
    padding: 10px 20px;
    width: 194px;
  }

  .getintouch {
    background-color: #f6961e;
    border-color: #f6961e;
  }

  .getintouch:hover {
    background-color: #89b83e;
    border-color: #89b83e;
  }

  .ordernow {
    background-color: #89b83e;
    border-color: #89b83e;
  }

  .ordernow:hover {
    background-color: #f6961e;
    border-color: #f6961e;
  }

  @media screen and (max-width: 991px) {
    #celery {
      left: 5% !important;
    }

    #herb {
      left: -3px !important;
      transform: rotate(45deg);
    }

    .quote {
      font-size: 45px;
    }

    #upper-leaf-quote {
      top: -23px;
    }

    #lower-leaf-quote {
      left: 218px;
    }
  }

  @media screen and (max-width: 767px) {
    #home {
      height: 100%;
      padding-bottom: 63px;
    }

    .headerlogo {
      display: block;
      margin-left: auto;
      margin-right: auto;
      margin-bottom: 20px;
    }

    .quote, .description {
      text-align: center;
    }

    #upper-leaf-quote, #lower-leaf-quote { 
      display:none;
    }

    .veggie-bowl {
      display: none;
    }

    .ctaButtons {
      display: flex;
      justify-content: center;
      align-items: center;
    }

    .cta {
      margin-left: 10px;
    }
  }

  @media screen and (max-width: 575px) {
    .quote {
      font-size: 40px;
    }

    #broccoli {
      bottom: 184px !important;
    }

    .cta {
      letter-spacing: normal;
      padding: 10px 10px;
    }
  }
</style>
