<template>
  <b-modal id="orderNowModal" size="lg" hide-footer>
    <div class="orderNowBackground"></div>
    <div class="orderNow">
      <img src="~/assets/images/odl-logo.png" class="modalLogo"/>
      <p>Our e-commerce website is still a work in progress. You can order directly thru an order form by clicking <span class="orderBtnGuide">"Order Now"</span> below. You can also view or download our price list by clicking <span class="orderBtnGuide">"View Pricelist"</span> below. Thank you!</p>
      <div class="orderNowButtons">
        <b-button pill href="/files/odl-pricelist.pdf" target="_blank" class="pricelistBtn" size="sm">View Pricelist <b-icon icon="arrow-right-square"></b-icon></b-button>
        <b-button pill href="https://form.jotform.com/212954127175053" target="_blank" class="pricelistBtn orderNowBtn" size="sm">Order Now <b-icon icon="cart-4"></b-icon></b-button>
      </div>
    </div>
  </b-modal>
</template>

<script>
import { BIcon, BIconCart4, BIconArrowRightSquare } from 'bootstrap-vue'

export default {
  name: 'OrderNowModal',
  components: {
    BIcon,
    BIconCart4,
    BIconArrowRightSquare
  }
}
</script>

<style>
  #orderNowModal .modal-body {
    height: 100%;
    width: 100%;
    display: flex;
    padding: 0;
  }

  .orderNowBackground {
    background-image: url('../../assets/images/order-now-modal-bg.jpg');
    background-size: cover;
    background-repeat: no-repeat;
    background-position: center;
    flex: 40%;
  }

  .orderNow {
    flex: 60%;
    background-color: #ffffff;
    padding: 30px 40px;
  }

  .modalLogo {
    width: 77px;
    height: 78px;
    display: block;
    margin-left: auto;
    margin-right: auto;
    margin-bottom: 20px;
  }

  .orderNow p {
    font-size: 16px;
    font-weight: 400;
    line-height: normal;
    text-align: justify;
    color: #3d3c3c;
    margin-bottom: 20px;
  }

  .orderNowButtons {
    display: flex;
    justify-content: flex-end;
    align-items: center;
  }

  .orderBtnGuide {
    font-weight: 600;
  }

  .pricelistBtn {
    background-color: #f6961e;
    border-color: #f6961e;
    color: #ffffff;
    font-size: 12px;
    font-weight: 700;
    text-transform: uppercase;
    padding: 10px 20px;
    margin-left: 5px;
    width: 197px;
  }

  .orderNowBtn {
    background-color: #89b83e;
    border-color: #89b83e;
  }

  @media screen and (max-width: 991px) {
    .orderNowBackground {
      display: none;
    }

    .orderNow {
      padding: 30px 20px;
    }

    .orderNowButtons {
      justify-content: center;
    }

    .pricelistBtn {
      padding: 10px 10px;
    }
  }

  @media screen and (max-width: 480px) {
    .orderNowButtons {
      flex-direction: column;
    }

    .pricelistBtn {
      margin-bottom: 10px;
    }
  }
</style>
