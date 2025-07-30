<script>
import { Swiper, SwiperSlide } from "swiper/vue";
import { Navigation, Pagination, Autoplay } from "swiper/modules";
import "swiper/css/bundle";

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
      modules: [Navigation, Pagination, Autoplay],
      // 选择要轮播的照片
      genie_manipulation_image_paths: [
        {
          src: "./carousel/manipulation/wipe-cut-o.gif",
          caption:
            "Use the sponge held in the right arm to wipe the stains clean",
        },
        {
          src: "./carousel/manipulation/sandwich-w-cut-o.gif",
          caption: "Make a sandwich",
        },
        {
          src: "./carousel/manipulation/conveyer-w-cut-o.gif",
          caption: "Pack washing detergent from the conveyor belt",
        },
        {
          src: "./carousel/manipulation/microwave-cut-o.gif",
          caption:
            "Close the open microwave door on the table with the left arm",
        },
      ],
      cross_manipulation_image_paths: [
        {
          src: "./carousel/manipulation/rollout1.gif",
          caption: "Fold the grey cloth",
        },
        {
          src: "./carousel/manipulation/rollout2.gif",
          caption: "Fold the grey cloth",
        },
        {
          src: "./carousel/manipulation/sl_cloth_pink.gif",
          caption: "Fold the pink cloth",
        },
        {
          src: "./carousel/manipulation/sl_box_2.gif",
          caption: "Fold the box",
        },
        {
          src: "./carousel/manipulation/franka_cloth.gif",
          caption: "Fold the cloth",
        },
      ],
      genie_generation_image_paths: [
        {
          src: "./carousel/generation/1148-16408-A2D0015AC00347-1054054.gif",
          caption: "Pick up the lettuce slice from the box on the table",
        },
        {
          src: "./carousel/generation/1170-16495-A2D0015AB00061-1056795.gif",
          caption:
            "Close the open microwave door on the table with the left arm",
        },
        {
          src: "./carousel/generation/352-5651-A2D0015AB00244-669797.gif",
          caption: "Pick up the milk from the refrigerator",
        },
        {
          src: "./carousel/generation/362-7584-A2D0015AC00163-734627.gif",
          caption:
            "Grasp the waistband of grey shorts and fold it down to the legs",
        },
        {
          src: "./carousel/generation/410-5526-A2D0015AC00150-661677.gif",
          caption: "Pour the water from the white kettle into the nearby cup",
        },
        {
          src: "./carousel/generation/765-11961-A2D0015AB00009-895006.gif",
          caption:
            "Move the white cleaner on the shelf to the position on the shelf",
        },
        {
          src: "./carousel/generation/779-12209-A2D0015AB00006-906599.gif",
          caption:
            "Pick up the seal from the inkpad on the table with right hand",
        },
        {
          src: "./carousel/generation/819-13215-A2D0015AB00009-948381.gif",
          caption:
            "Use the sponge held in the right arm to wipe the stains clean",
        },
        {
          src: "./carousel/generation/951-14176-A2D0001AB00023-1012800.gif",
          caption:
            "Throw the trash on the desktop into the trash can on the right",
        },
        {
          src: "./carousel/generation/951-14179-A2D0015AC00305-1013249.gif",
          caption:
            "Throw the trash on the desktop into the trash can on the right",
        },
      ],
      cross_generation_image_paths: [
        {
          src: "./carousel/generation/Validation_slow_1.gif",
          caption: "Fold the blue cloth",
        },
        {
          src: "./carousel/generation/Validation_slow_2.gif",
          caption: "Fold the grey cloth",
        },
        {
          src: "./carousel/generation/Validation_slow_3.gif",
          caption: "Fold the blue cloth",
        },
        {
          src: "./carousel/generation/Validation_slow_4.gif",
          caption: "Fold the green cloth",
        },
        {
          src: "./carousel/generation/franka_cloth_gen_2.gif",
          caption: "Fold the blue cloth",
        },
      ],
    };
  },
  computed: {
    firstGenieGenImages() {
      return this.genie_generation_image_paths.filter(
        (_, index) => index % 2 === 0
      );
    },
    secondGenieGenImages() {
      return this.genie_generation_image_paths.filter(
        (_, index) => index % 2 === 1
      );
    },
    firstCrossGenImages() {
      return this.cross_generation_image_paths.filter(
        (_, index) => index % 2 === 0
      );
    },
    secondCrossGenImages() {
      return this.cross_generation_image_paths.filter(
        (_, index) => index % 2 === 1
      );
    },
  },
};
</script>

<template>
  <el-row justify="center" class="section-title">
    <h1>AgiBot-G1</h1>
  </el-row>

  <el-row justify="center" style="margin-right: 5%; margin-left: 5%">
    <el-col
      :xs="24"
      :sm="20"
      :md="16"
      :lg="12"
      :xl="12"
      style="min-height: 400px; display: flex; justify-content: flex-end"
    >
      <div class="double-swiper">
        <span class="label">Video Generation</span>
        <swiper
          ref="genie_swiper1"
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          :pagination="{
            hideOnClick: true,
            clickable: true,
            type: 'bullets',
          }"
          :autoplay="{
            delay: 2400,
            disableOnInteraction: false,
            pauseOnMouseEnter: true,
          }"
          class="swiper-generation"
        >
          <swiper-slide
            v-for="(item, index) in firstGenieGenImages"
            class="slide, slide_left"
            :key="index"
          >
            <div class="image-caption-wrapper">
              <el-image :src="item.src" />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
        <swiper
          ref="genie_swiper2"
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          :pagination="{
            hideOnClick: true,
            clickable: true,
            type: 'bullets',
          }"
          :autoplay="{
            delay: 2400,
            disableOnInteraction: false,
            pauseOnMouseEnter: true,
          }"
          class="swiper-generation"
        >
          <swiper-slide
            v-for="(item, index) in secondGenieGenImages"
            class="slide, slide_left"
            :key="index"
          >
            <div class="image-caption-wrapper">
              <el-image :src="item.src" />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>

    <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
      <div class="right-swiper">
        <span class="label">Manipulation</span>
        <swiper
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          :pagination="{
            hideOnClick: true,
            clickable: true,
            type: 'bullets',
          }"
          :autoplay="{
            delay: 2400,
            disableOnInteraction: false,
            pauseOnMouseEnter: true,
          }"
        >
          <swiper-slide
            v-for="(item, index) in genie_manipulation_image_paths"
            :key="index"
            class="slide, slide_right"
          >
            <div class="image-caption-wrapper">
              <el-image :src="item.src" />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>
  </el-row>

  <el-row justify="center" class="section-title">
    <h1>Cross Embodiment</h1>
  </el-row>

  <el-row justify="center" style="margin-right: 5%; margin-left: 5%">
    <el-col
      :xs="24"
      :sm="20"
      :md="16"
      :lg="12"
      :xl="12"
      style="min-height: 400px; display: flex; justify-content: flex-end"
    >
      <div class="double-swiper">
        <span class="label">Video Generation</span>
        <swiper
          ref="genie_swiper1"
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          :pagination="{
            hideOnClick: true,
            clickable: true,
            type: 'bullets',
          }"
          :autoplay="{
            delay: 2400,
            disableOnInteraction: false,
            pauseOnMouseEnter: true,
          }"
          class="swiper-generation"
        >
          <swiper-slide
            v-for="(item, index) in firstCrossGenImages"
            class="slide, slide_left"
            :key="index"
          >
            <div class="image-caption-wrapper">
              <el-image :src="item.src" />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>

        <swiper
          ref="genie_swiper2"
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          :pagination="{
            hideOnClick: true,
            clickable: true,
            type: 'bullets',
          }"
          :autoplay="{
            delay: 2400,
            disableOnInteraction: false,
            pauseOnMouseEnter: true,
          }"
          class="swiper-generation"
        >
          <swiper-slide
            v-for="(item, index) in secondCrossGenImages"
            class="slide, slide_left"
            :key="index"
          >
            <div class="image-caption-wrapper">
              <el-image :src="item.src" />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>
    <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
      <div class="right-swiper">
        <span class="label">Manipulation</span>
        <swiper
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          :pagination="{
            hideOnClick: true,
            clickable: true,
            type: 'bullets',
          }"
          :autoplay="{
            delay: 10000,
            disableOnInteraction: false,
            pauseOnMouseEnter: true,
          }"
          class="swiper-manipulation"
        >
          <swiper-slide
            v-for="item in cross_manipulation_image_paths"
            class="slide, slide_right"
            :key="item"
          >
            <div class="image-caption-wrapper">
              <el-image :src="item.src" />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>
  </el-row>
</template>

<style>
.swiper {
  --swiper-theme-color: white;
  position: relative;
  max-width: 100%;
  max-width: 100%;
}

.sbox {
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  align-items: center;
  width: 95%;
}

.slide_left {
  justify-content: center;
}

.slide_right {
  justify-content: center;
}

.swiper-slide {
  display: flex;
  align-items: center;
  /* height: 100%; */
  min-width: 30%;
}

.double-swiper {
  display: block;
  /* float: right; */
  /* flex-direction: column; */
  height: 95%;
  max-width: 60%;
  margin-left: 35%;

  margin-right: 10px;
  align-items: center;
}
.right-swiper {
  display: block;
  /* float: right; */
  /* flex-direction: column; */
  height: 95%;
  max-width: 60%;
  margin-right: 35%;
  margin-left: 10px;
  align-items: center;
  object-fit: contain;
}
.slide img {
  width: 100%;
  height: 100%;
  border-radius: 8px;
  margin: 10px;
  display: block;
  /* display: flex;
  justify-content: flex-end; */
}
.swiper-generation {
  width: 100%;
}
.section-title {
  margin: 20px 0;
}
.swiper-button-prev,
.swiper-button-next {
  color: white;
}

/* 控制按钮位置 */
.swiper-button-prev {
  left: 25px; /* 向内移动10px */
  top: 45%;
}

.swiper-button-next {
  right: 25px;
  top: 45%;
}
.label {
  color: #7e8481;
  font-family: "MyFont", Verdana, sans-serif;
  display: block; /* span 默认是 inline，改成 block 才能使用 text-align */
  text-align: center;
  margin-top: 5px; /* 可选 */
  margin-bottom: 10px;
  font-size: 20px;
}
.image-caption-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.caption {
  margin-top: 3px;
  margin-bottom: 2px;
  font-size: 17px;
  font-family: "Gill Sans", sans-serif;
  font-style: italic;
  color: #333;
  text-align: center;
}

.swiper-pagination {
  margin-top: 14px;
  position: relative;
  display: none !important;
}

.double-swiper .swiper-pagination {
  /* margin-top: 14px;  */
  /* position: relative; */
  display: none !important;
}
</style>
