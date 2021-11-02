<template>
  <div id="app">
    <Swiper
      :loop="true"
      :direction="vertical"
      :autoplay="{ delay: 500 }"
      :pagination="{ el: '.swiper-pagination' }"
      :slidesPerView="2"
      :slidesPerGroup="2"
      :swiperData="swiperList"
    >
      <template v-slot:swiper-slides>
        <div v-for="item in swiperList" :key="item.id" class="swiper-slide">
          <img :src="item.imgurl" :alt="item.alt">
          <p>{{item.alt}}</p>
        </div>
      </template>
    </Swiper>
    <Swiper
      :loop="true"
      :direction="vertical"
      :autoplay="{ delay: 500 }"
      :pagination="{ el: '.swiper-pagination' }"
      :slidesPerView="1"
      :slidesPerGroup="1"
      :swiperData="swiperList"
    >
      <template v-slot:swiper-slides>
        <div v-for="item in swiperList" :key="item.id" class="swiper-slide">
          <img :src="item.imgurl" :alt="item.alt">
          <p>{{item.alt}}</p>
        </div>
      </template>
    </Swiper>
  </div>
</template>

<script>
import Swiper from "./components/Swiper.vue";
export default {
  name: "App",
  components: {
    Swiper,
  },
  data() {
    return {
      swiperList: [
        {
          id: "001",
          imgurl: require("./assets/logo.png"),
          alt: "logo",
        },
        {
          id: "002",
          imgurl: require("./assets/logo.png"),
          alt: "logo",
        },
        {
          id: "003",
          imgurl: require("./assets/logo.png"),
          alt: "logo",
        },
        {
          id: "004",
          imgurl: require("./assets/logo.png"),
          alt: "logo",
        },
      ],
      swiperOption: {
        autoplay: {
          delay: 500,
        },
        loop: true,
        pagination: {
          el: ".swiper-pagination",
        },
        effect: "coverflow",
      },
    };
  },
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
