<template>
  <div id="gallery">
    <b-container>
      <div class="gallery-images">
        <vue-slick-carousel v-bind="carousel" v-if="galleryImages.length != 0">
          <div class="gallery-image" v-for="gallery in galleryImages" :key="gallery.image">
            <img :src="require(`~/static${gallery.image}`)"/>
          </div>
        </vue-slick-carousel>
      </div>
    </b-container>
  </div>
</template>

<script>
import VueSlickCarousel from 'vue-slick-carousel'
import 'vue-slick-carousel/dist/vue-slick-carousel.css'
import 'vue-slick-carousel/dist/vue-slick-carousel-theme.css'

export default {
  name: 'Gallery',
  components: {
    VueSlickCarousel
  },
  data() {
    return {
      galleryImages: [],
      carousel: {
        arrows: true,
        dots: true,
        infinite: true,
        rows: 2,
        slidesToShow: 3,
        slidesPerRow: 1,
        speed: 500,
        autoplay: true,
        autoplaySpeed: 5000,
        pauseOnDotsHover: true,
        pauseOnFocus: true,
        pauseOnHover: true
      }
    }
  },
  mounted() {
    this.getGalleryImages()
  },
  methods: {
    async getGalleryImages() {
      this.galleryImages = await this.$content('gallery').fetch()
    }
  }
}
</script>

<style>
  #gallery {
    width: 100%;
    height: 600px;
  }

  .gallery-images {
    padding: 56px 0;
  }

  .gallery-image img {
    height: 241px;
    width: 100%;
    padding: 5px;
  }

  .slick-prev::before, .slick-next::before {
    color: #1e1c1c;
  }

  @media screen and (max-width: 991px) {
    #gallery {
      height: 100%;
    }
  }
</style>
