<template>
  <div id="gallery">
    <b-container>
      <h2>Gallery</h2>
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
        slidesToScroll: 3,
        speed: 1000,
        autoplay: true,
        autoplaySpeed: 3000,
        pauseOnDotsHover: true,
        pauseOnFocus: true,
        pauseOnHover: true,
        responsive: [
          {
            breakpoint: 991,
            settings: {
              slidesToShow: 2,
              slidesToScroll: 2
            }
          },
          {
            breakpoint: 480,
            settings: {
              slidesToShow: 1,
              slidesToScroll: 1,
              rows: 1,
              dots: false
            }
          }
        ]
      }
    }
  },
  mounted() {
    this.getGalleryImages()
  },
  methods: {
    async getGalleryImages() {
      this.galleryImages = await this.$content('gallery').sortBy('image').fetch()
    }
  }
}
</script>

<style>
  #gallery {
    width: 100%;
    height: 600px;
  }

  #gallery h2 {
    font-weight: 700;
    font-size: 24px;
    color: #89b83e;
    letter-spacing: 0.2em;
    text-transform: uppercase;
    margin: 30px 0;
  }

  .gallery-images {
    padding-bottom: 56px;
  }

  .gallery-image img {
    height: 241px;
    width: 100%;
    padding: 5px;
    object-fit: cover;
    -o-object-fit: cover;
  }

  .slick-prev::before, .slick-next::before {
    color: #1e1c1c !important;
  }

  @media screen and (max-width: 991px) {
    #gallery {
      height: 100%;
    }

    .gallery-image img {
      height: 360px;
    }
  }

  @media screen and (max-width: 576px) {
    #gallery {
      padding-left: 20px;
      padding-right: 20px;
    }
  }

  @media screen and (max-width: 480px) {
    .gallery-images {
      padding-bottom: 0;
    }
  }
</style>
