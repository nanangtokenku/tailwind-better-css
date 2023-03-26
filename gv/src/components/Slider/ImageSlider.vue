<template>
    <div class="swiper-container">
      <div class="swiper-wrapper">
        <div class="swiper-slide" v-for="image in images" :key="image.id">
          <img :src="image.src" alt="">
        </div>
      </div>
      <div class="swiper-pagination"></div>
    </div>
  </template>
  
  <script>
  import Swiper from 'swiper';
  
  export default {
    name: 'ImageSlider',
    props: {
      images: {
        type: Array,
        required: true
      }
    },
    mounted() {
      this.swiper = new Swiper('.swiper-container', {
        pagination: {
          el: '.swiper-pagination',
        },
      });
    },
    beforeUnmount() {
      if (this.swiper) {
        this.swiper.destroy();
        this.swiper = null;
      }
    }
  }
  </script>
  
  <style>
  /* Optional styling */
  .swiper-container {
    width: 100%;
    height: 100%;
  }
  .swiper-slide img {
    width: 100%;
    height: 100%;
    object-fit: cover;
  }
  </style>
  