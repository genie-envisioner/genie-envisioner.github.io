<script>
import { Swiper, SwiperSlide } from 'swiper/vue';
import { Navigation, Pagination, Autoplay } from 'swiper/modules';
import 'swiper/css/bundle';

export default {
  components: {
    Swiper,
    SwiperSlide,
    Navigation,
    Pagination,
    Autoplay,
  },
  data() {
    return {
      modules: [
        Navigation,
        Pagination,
        Autoplay,
      ],
      // 选择要轮播的照片
      agi_manipulation_image_paths: [
        "./carousel/manipulation/wipe-cut-o.gif",
        "./carousel/manipulation/sandwich-w-cut-o.gif",
        "./carousel/manipulation/conveyer-w-cut-o.gif",
        "./carousel/manipulation/microwave-cut-o.gif",
      ],
      other_manipulation_image_paths: [
         "./carousel/manipulation/rollout1.gif",
        "./carousel/manipulation/rollout2.gif",
      ],
      agi_generation_image_paths: [
        "./carousel/generation/1148-16408-A2D0015AC00347-1054054.gif",
        "./carousel/generation/1170-16495-A2D0015AB00061-1056795.gif",
        "./carousel/generation/352-5651-A2D0015AB00244-669797.gif",
        "./carousel/generation/362-7584-A2D0015AC00163-734627.gif",
        "./carousel/generation/410-5526-A2D0015AC00150-661677.gif",
        "./carousel/generation/765-11961-A2D0015AB00009-895006.gif",
        "./carousel/generation/779-12209-A2D0015AB00006-906599.gif",
        "./carousel/generation/819-13215-A2D0015AB00009-948381.gif",
        "./carousel/generation/951-14176-A2D0001AB00023-1012800.gif",
        "./carousel/generation/951-14179-A2D0015AC00305-1013249.gif",
      ],
      other_generation_image_paths: [
        "./carousel/generation/Validation_slow_1.gif",
        "./carousel/generation/Validation_slow_2.gif",
        "./carousel/generation/Validation_slow_3.gif",
        "./carousel/generation/Validation_slow_4.gif",
      ],
    }
  }
}
</script>

<template>
  <el-row justify="center" class="section-title">
    <h1>Generation</h1> 
  </el-row>

  <el-row justify="center">

    <el-col :span="9" style="margin: 10px 5px 0px 0px;" >
      <!-- 设置轮播图：循环播放、首张图序号、响应式、导航和分页、自动播放 -->
      <swiper :loop="true" :slidesPerView="1" :breakpoints="{
        600: {
          slidesPerView: 1,
        },
        800: {
          slidesPerView: 1,
        },
      }" :modules="modules" :navigation="{
        hideOnClick: true,
      }" :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 2400,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }" class="swiper-generation">
        <swiper-slide v-for="path in agi_generation_image_paths" class="slide">
          <el-image  :src="path" />
        </swiper-slide>
      </swiper>
      <span class="label">AgiBot</span> 
    </el-col>

    <el-col :span="9" style="margin: 10px 0px 0px 5px;">
      <!-- 设置轮播图：循环播放、首张图序号、响应式、导航和分页、自动播放 -->
      <swiper :loop="true" :slidesPerView="1" :breakpoints="{
        600: {
          slidesPerView: 1,
        },
        800: {
          slidesPerView: 1,
        },
      }" :modules="modules" :navigation="{
        hideOnClick: true,
      }" :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 2400,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }">
        <swiper-slide v-for="path in other_generation_image_paths" class="slide">
          <el-image :src="path" />
        </swiper-slide>
      </swiper>
      <span class="label">Other</span> 
    </el-col>
  </el-row>

  <el-row justify="center" class="section-title">
    <h1>Manipulation</h1> 
  </el-row>

  <el-row justify="center">

    <el-col :span="9" style="margin: 10px 10px 0px 0px;">
      <!-- 设置轮播图：循环播放、首张图序号、响应式、导航和分页、自动播放 -->
      <swiper :loop="true" :slidesPerView="1" :breakpoints="{
        600: {
          slidesPerView: 1,
        },
        800: {
          slidesPerView: 1,
        },
      }" :modules="modules" :navigation="{
        hideOnClick: true,
      }" :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 10000,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }">
        <swiper-slide v-for="path in agi_manipulation_image_paths" class="slide">
          <el-image :src="path" />
        </swiper-slide>
      </swiper>
      <span class="label">AgiBot</span> 
    </el-col>

    <el-col :span="9" style="margin: 10px 0px 0px 10px;">
      <!-- 设置轮播图：循环播放、首张图序号、响应式、导航和分页、自动播放 -->
      <swiper :loop="true" :slidesPerView="1" :breakpoints="{
        600: {
          slidesPerView: 1,
        },
        800: {
          slidesPerView: 1,
        },
      }" :modules="modules" :navigation="{
        hideOnClick: true,
      }" :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 10000,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }" class="swiper-manipulation">
        <swiper-slide v-for="path in other_manipulation_image_paths" class="slide">
          <el-image :src="path" />
        </swiper-slide>
      </swiper>
      <span class="label">Other</span> 
    </el-col>
  </el-row>
</template>

<style>
/* 设置Swiper风格 */
.swiper {
  --swiper-theme-color: white;
  position: relative;
  width: 100%;
}
.swiper-button-next {
  right: 10px;
}
.slide img {
  width: 100%;
  border-radius: 8px;
  display: block;
  /* box-shadow: 0 rgba(0,0,0,0.1); */
}
.section-title {
  margin: 10px 0;
}
.label {
  color: #7e8481;
  font-family: "MyFont", Verdana, sans-serif;
}
</style>