<template>
  <div class="swiper-container">
    <div class="swiper-wrapper">
      <slot name="swiper-slides"></slot>
    </div>
    <div class="swiper-pagination"></div>
  </div>
</template>

<script>
import Swiper from "swiper";
import 'swiper/dist/css/swiper.min.css'
export default {
  name: "Swiper",
  props: {
    //  是否循环
    loop: {
      type: Boolean,
      default: false,
    },
    // 自动播放
    autoplay: {
      type: Object || Boolean,
      default: false,
    },
    // 轮播方向
    direction: {
      type: String,
      default: "horizontal",
    },
    // 小圆点指示器
    pagination: {
      type: Object,
      default: function () {
        return {
          el: "swiper-pagination",
        };
      },
    },
    // 轮播效果
    effect: {
      type: String,
      default: "slide",
    },
    // 一屏展示几张
    slidesPerView: {
      type: Number,
      default: 1,
    },
    // 一次轮播几张
    slidesPerGroup: {
      type: Number,
      default: 1,
    }
  },
  mounted() {
    new Swiper('.swiper-container',this.getOption())
  },
  methods: {
    getOption() {
      let option = {};

      option.loop = this.loop;
      option.autoplay = this.autoplay;
      option.direction = this.direction;
      option.pagination = this.pagination;
      option.effect = this.effect;
      option.slidesPerView = this.slidesPerView;
      option.slidesPerGroup = this.slidesPerGroup;

      return option;
    },
  },
};
</script>

<style>
</style>