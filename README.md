# 自封装swiper组件（暂未命名）

## 开发原因？

vue-awesome-swiper（**以下简称swiper-vue**）是一个很不错的swiper包应用于vue开发中，但是在使用swiper-vue的时候，对照着swiper官方文档进行调试过程中，出现了许多属性设置后无法实现效果的情况。

在这种情况，第一反应就是swiper的版本太高，可能文档更新不及时。需要降低swiper的版本。swiper-vue官方文档中提供的低版本下载应用到了项目中。指令失效问题依旧无解，不生效。

无奈之下，准备自己封装一个自己使用。

## 版本情况？

- swiper 基于官方V4最终版：`4.5.1`
- 该swiper组件开发基于vue V2版本：`2.6.11`

## 使用方法？

1. 在项目中下载Swiper 4.5.1 版本

   ```shell
   npm install swiper@4.5.1 -S
   ```

   

2. 点击 [Releases]([Releases · xxxzl-JerryM/Jerry.M_swiper (github.com)](https://github.com/xxxzl-JerryM/Jerry.M_swiper/releases)) 页面，看到最新版本，下载 Assets 模块中的 `Swiper.vue` 文件

3. 下载之后将其放入需要的项目**/src/components**内

4. 在需要轮播图的页面（组件）内引入 Swiper.vue 并且注册

   ```js
   import Swiper from ‘@/src/components/Swiper'
   
   export default{
       components:{
           Swiper
       }
   }
   ```

5. 在 `<template></template>`中使用

   ```vue
   <template>
     <div id="app">
       <Swiper
         :loop="true"
         :autoplay="{ delay: 500 }"
         :pagination="{ el: '.swiper-pagination' }"
         :slidesPerView="2"
         :slidesPerGroup="2"
       >
         <template v-slot:swiper-slides></template>
       </Swiper>
     </div>
   </template>
   ```

   - 可传入配置项：

     1. loop：
        作用：控制轮播图能否循环播放
        类型：Boolean
        默认：false

     2. autoplay：
        作用：控制轮播图能否自动播放
        类型：Object || Boolean
        默认：false

     3. pagination：
        作用：控制轮播图指示器（小圆点）
        类型：Object
        默认：

        ```js
        {
          el: "swiper-pagination",
        }
        ```

     4. slidesPerView:
        作用：控制轮播在一屏上显示几个slide
        类型：Number
        默认：1
     5. slidesPerGroup：
        作用：控制一次播放几张
        类型：Number
        默认：1
     6. effect：
        作用：控制轮播图切换的样式
        类型：String
        默认：'slide'

   - 插槽：

     1. swiper-slides
        作用：由使用者自己传入需要展示的内容

        案例展示：

        ```vue
        <!--使用v-for进行条件渲染-->
        <template v-slot:swiper-slides>
            <div v-for="item in swiperList" :key="item.id" class="swiper-slide">
                <img :src="item.imgurl" :alt="item.alt">
                <p>{{item.alt}}</p>
            </div>
        </template>
        ```

        ```js
        // 条件渲染需要的数据
        export default {
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
        }
        ```

## 其他参考？

1. vue 官方文档：[Vue.js (vuejs.org)](https://cn.vuejs.org/)
2. swiper官方文档：[Swiper中文网-轮播图幻灯片js插件,H5页面前端开发](https://swiper.com.cn/)
