<template>
  <b-modal id="orderNowModal" size="lg" hide-footer>
    <div class="orderNowBackground"></div>
    <div class="orderNow">
      <img src="~/assets/images/odl-logo.png" class="modalLogo"/>
      <p>Our e-commerce website is still a work in progress. You can view or download our pricelist here and send us a message to order.  Thank you!</p>
      <div class="orderNowBtn">
        <b-button pill href="/files/odl-pricelist.pdf" download class="pricelistBtn" size="sm">Download Pricelist <b-icon icon="download"></b-icon></b-button>
        <b-button pill href="/files/odl-pricelist.pdf" target="_blank" class="pricelistBtn" size="sm">View Pricelist <b-icon icon="arrow-right-square"></b-icon></b-button>
      </div>
    </div>
  </b-modal>
</template>

<script>
import { BIcon, BIconDownload, BIconArrowRightSquare } from 'bootstrap-vue'

export default {
  name: 'OrderNowModal',
  components: {
    BIcon,
    BIconDownload,
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

  .orderNowBtn {
    display: flex;
    justify-content: flex-end;
    align-items: center;
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

  @media screen and (max-width: 991px) {
    .orderNowBackground {
      display: none;
    }

    .orderNow {
      padding: 30px 20px;
    }

    .orderNowBtn {
      justify-content: center;
    }

    .pricelistBtn {
      padding: 10px 10px;
    }
  }

  @media screen and (max-width: 480px) {
    .orderNowBtn {
      flex-direction: column;
    }

    .pricelistBtn {
      margin-bottom: 10px;
    }
  }
</style>
