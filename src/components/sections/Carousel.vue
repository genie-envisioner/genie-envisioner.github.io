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
      genie_manipulation_image_paths: [
        "./carousel/manipulation/wipe-cut-o.gif",
        "./carousel/manipulation/sandwich-w-cut-o.gif",
        "./carousel/manipulation/conveyer-w-cut-o.gif",
        "./carousel/manipulation/microwave-cut-o.gif",
      ],
      cross_manipulation_image_paths: [
        "./carousel/manipulation/rollout1.gif",
        "./carousel/manipulation/rollout2.gif",
        "./carousel/manipulation/sl_cloth_pink.gif",
        "./carousel/manipulation/sl_box_2.gif",
        "./carousel/manipulation/franka_cloth.gif",
      ],
      genie_generation_image_paths: [
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
      cross_generation_image_paths: [
        "./carousel/generation/Validation_slow_1.gif",
        "./carousel/generation/Validation_slow_2.gif",
        "./carousel/generation/Validation_slow_3.gif",
        "./carousel/generation/Validation_slow_4.gif",
        "./carousel/generation/franka_cloth_gen_2.gif",
      ],
    }
  },
  computed: {
    firstGenieGenImages() {
      return this.genie_generation_image_paths.filter((_, index) => index % 2 === 0)
    },
    secondGenieGenImages() {
      return this.genie_generation_image_paths.filter((_, index) => index % 2 === 1)
    },
    firstCrossGenImages() {
      return this.cross_generation_image_paths.filter((_, index) => index % 2 === 0)
    },
    secondCrossGenImages() {
      return this.cross_generation_image_paths.filter((_, index) => index % 2 === 1)
    },
  },
}
</script>

<template>
  <el-row justify="center" class="section-title">
    <h1>Genie-01</h1> 
  </el-row>

  <el-row justify="center">

    <div class="left-box">
      <div class="double-swiper">
      <swiper ref="genie_swiper1" :loop="true" :slidesPerView="1" :modules="modules" :navigation="{
        hideOnClick: true,
      }"
        :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 2400,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }" 
        class="swiper-generation">
        <swiper-slide v-for="(path, index) in firstGenieGenImages" class="slide" :key="index">
          <el-image  :src="path" />
        </swiper-slide>
      </swiper>

      <swiper ref="genie_swiper2" :loop="true" :slidesPerView="1" :modules="modules" :navigation="{
        hideOnClick: true,
      }"
        :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 2400,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }" 
        style="margin: 15px 0px 0px 0px;"
        class="swiper-generation">
        <swiper-slide v-for="(path, index) in secondGenieGenImages" class="slide" :key="index">
          <el-image  :src="path" />
        </swiper-slide>
      </swiper>
      </div>
      <span class="label">Video Generation</span> 
    </div>

    <div class="right-box">
      <swiper :loop="true" :slidesPerView="1" :modules="modules" :navigation="{
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
        <swiper-slide v-for="path in genie_manipulation_image_paths" class="slide">
          <el-image :src="path" />
        </swiper-slide>
      </swiper>
      <span class="label">Manipulation</span> 
    </div>
  </el-row>

  <el-row justify="center" class="section-title">
    <h1>Cross Embodiment</h1> 
  </el-row>

  <el-row justify="center">

    <div class="left-box">
      <div class="double-swiper" style="height: 95%; width: 700px">
      <swiper ref="genie_swiper1" :loop="true" :slidesPerView="1" :modules="modules" :navigation="{
        hideOnClick: true,
      }"
        :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 2400,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }" 
        class="swiper-generation">
        <swiper-slide v-for="(path, index) in firstCrossGenImages" class="slide" :key="index">
          <el-image  :src="path" />
        </swiper-slide>
      </swiper>

      <swiper ref="genie_swiper2" :loop="true" :slidesPerView="1" :modules="modules" :navigation="{
        hideOnClick: true,
      }"
        :pagination="{
          hideOnClick: true,
          clickable: true,
          type: 'bullets'
        }" :autoplay="{
          delay: 2400,
          disableOnInteraction: false,
          pauseOnMouseEnter: true,
        }" 
        style="margin: 15px 0px 0px 0px;"
        class="swiper-generation">
        <swiper-slide v-for="(path, index) in secondCrossGenImages" class="slide" :key="index">
          <el-image  :src="path" />
        </swiper-slide>
      </swiper>
      </div>
      <span class="label">Video Generation</span> 
    </div>
    <div class="right-box">
      <swiper :loop="true" :slidesPerView="1" :modules="modules" :navigation="{
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
        <swiper-slide v-for="path in cross_manipulation_image_paths" class="slide">
          <el-image :src="path" />
        </swiper-slide>
      </swiper>
      <span class="label">Manipulation</span> 
    </div>
  </el-row>
</template>

<style>
/* 设置Swiper风格 */

.swiper {
  --swiper-theme-color: white;
  position: relative;
  width: 600px;
}
.swiper-button-next {
  right: 10px;
}
.swiper-manipulation {
  margin: 0;   
  padding: 0;
}
.left-box {
  flex: 1;
  padding: 10px;
  margin-left: 15%;
  max-width: 30%;
  justify-content: right
}
.right-box {
  /* flex: 1; */
  display: flex;
  flex-direction: column;
  padding: 10px;
  margin-right: 15%;
  /* justify-content: left */
  
}
.double-swiper {
  display: flex;
  flex-direction: column;
  height: 95%;
  width: 700px;
}
.slide img {
  width: 100%;
  border-radius: 8px;
  margin: 0;
  display: block;
}
.swiper-generation { width: 100%; }
.section-title {
  margin: 20px 0;
}
.label {
  color: #7e8481;
  font-family: "MyFont", Verdana, sans-serif;
}

</style>