<template>
  <div id="gallery">
    <b-container>
      <b-row align-h="center" align-v="center" class="gallery-row">
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
      </b-row>
      <b-row align-h="center" align-v="center" class="gallery-row">
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
      </b-row>
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
    margin-bottom: 40px;
  }

  .gallery-row {
    padding-top: 56px;
  }

  .gallery-image {
    margin-right: 10px;
    position: relative;
    height: 100%;
  }

  .gallery-image img {
    height: 241px;
    width: 241px;
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
</style>
