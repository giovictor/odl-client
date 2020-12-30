<template>
  <div id="gallery">
    <b-container>
      <div class="gallery-row">
        <div class="gallery-image">
          <img :src="require(`~/assets/images/delivery.jpg`)"/>
          <div class="gallery-image-text">delivery</div>
        </div>
        <div class="gallery-image">
          <img :src="require(`~/assets/images/farmer.jpg`)"/>
          <div class="gallery-image-text">farmer</div>
        </div>
        <div class="gallery-image">
          <img :src="require(`~/assets/images/farm.jpg`)"/>
          <div class="gallery-image-text">farm</div>
        </div>
        <div class="gallery-image">
          <img :src="require(`~/assets/images/nature.jpg`)"/>
          <div class="gallery-image-text">nature</div>
        </div>
        <div class="gallery-image">
          <img :src="require(`~/assets/images/landscape.jpg`)"/>
          <div class="gallery-image-text">landscape</div>
        </div>
        <div class="gallery-image">
          <img :src="require(`~/assets/images/products.jpg`)"/>
          <div class="gallery-image-text">products</div>
        </div>
      </div>
    </b-container>
  </div>
</template>

<script>
export default {
  name: 'Gallery'
}
</script>

<style>
  #gallery {
    width: 100%;
    height: 600px;
  }

  .gallery-row {
    padding: 56px 0;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-wrap: wrap;
  }

  .gallery-image {
    margin-right: 10px;
    margin-bottom: 10px;
    position: relative;
    height: 100%;
    flex: 30%;
  }

  .gallery-image img {
    height: 241px;
    width: 100%;
    display: block;
    margin: 0 auto;
  }

  .gallery-image-text {
    position: absolute;
    height: 100%;
    width: 100%;
    left: 0;
    top: 0;
    background-color: #454545;
    opacity: 0.9;
    text-transform: uppercase;
    color: #ffffff;
    display: flex;
    justify-content: center;
    align-items: center;
    font-size: 21px;
    letter-spacing: 0.2em;
    transition: all 0.4s ease-in-out;
  }

  .gallery-image:hover .gallery-image-text {
    opacity: 0;
  }

  @media screen and (max-width: 991px) {
    #gallery {
      height: 100%;
    }

    .gallery-image {
      flex: 48%;
    }
  }
</style>
