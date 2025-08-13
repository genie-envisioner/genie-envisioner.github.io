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
      first_line: [" ", " "],
      second_line: [" ", " "],
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
          src: "./carousel/manipulation/fold-stamp.gif",
          caption:
            "Fold a box, place the candy inside, seal and apply the stamp.",
        },
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
  methods: {
    onCrossRightSlideInit(s) {
      const index = s.realIndex;
      if (this.cross_manipulation_image_paths[index]) {
        this.second_line[1] =
          this.cross_manipulation_image_paths[index].caption;
      } else {
        this.second_line[1] = "";
      }
    },
    onCrossLeftSlideInit(s) {
      const index = s.realIndex;
      if (this.secondCrossGenImages[index]) {
        this.second_line[0] = this.secondCrossGenImages[index].caption;
      } else {
        this.second_line[0] = "";
      }
    },
    onG1LeftSlideInit(s) {
      const index = s.realIndex;
      if (this.secondGenieGenImages[index]) {
        this.first_line[0] = this.secondGenieGenImages[index].caption;
      } else {
        this.first_line[0] = "";
      }
    },
    onG1RightSlideInit(s) {
      const index = s.realIndex;
      if (this.genie_manipulation_image_paths[index]) {
        this.first_line[1] = this.genie_manipulation_image_paths[index].caption;
      } else {
        this.first_line[1] = "";
      }
    },
    onG1LeftSlideChange(s) {
      const index = s.realIndex;
      if (this.genie_generation_image_paths[index]) {
        this.first_line[0] = this.secondGenieGenImages[index].caption;
      } else {
        this.first_line[0] = "";
      }
    },
    onG1RightSlideChange(s) {
      const index = s.realIndex;
      if (this.genie_manipulation_image_paths[index]) {
        this.first_line[1] = this.genie_manipulation_image_paths[index].caption;
      } else {
        this.first_line[1] = "";
      }
    },
    onCrossLeftSlideChange(s) {
      const index = s.realIndex;
      if (this.secondCrossGenImages[index]) {
        this.second_line[0] = this.secondCrossGenImages[index].caption;
      } else {
        this.second_line[0] = "";
      }
    },
    onCrossRightSlideChange(s) {
      const index = s.activeIndex;

      if (this.cross_manipulation_image_paths[index]) {
        this.second_line[1] =
          this.cross_manipulation_image_paths[index].caption;
      } else {
        this.second_line[1] = "";
      }
    },
  },
};
</script>

<template>
  <el-divider />

  <el-row justify="center" class="section-title">
    <h1 class="section-title-h1">AgiBot-G1</h1>
  </el-row>

  <el-row justify="center" style="margin-right: 5%; margin-left: 5%">
    <el-col
      :xs="24"
      :sm="12"
      :md="12"
      :lg="12"
      :xl="12"
      style="display: flex; justify-content: center"
    >
      <div class="double-swiper">
        <div class="double-swiper-inner">
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
                <el-image
                  :src="item.src"
                  class="responsive-image"
                  fit="contain"
                />
                <div class="caption">{{ item.caption }}</div>
              </div>
            </swiper-slide>
          </swiper>
        </div>
        <swiper
          ref="genie_swiper2"
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          @swiper="onG1LeftSlideInit"
          @slideChange="onG1LeftSlideChange"
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
              <el-image
                :src="item.src"
                class="responsive-image"
                fit="contain"
              />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>

    <el-col :xs="24" :sm="12" :md="12" :lg="12" :xl="12">
      <div class="right-swiper">
        <span class="label">Manipulation</span>
        <swiper
          ref="agi_right_swiper"
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
          @swiper="onG1RightSlideInit"
          @slideChange="onG1RightSlideChange"
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
              <el-image
                :src="item.src"
                class="responsive-image"
                fit="contain"
              />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>
  </el-row>

  <el-row justify="center" class="section-title">
    <h1 class="section-title-h1">Cross Embodiment</h1>
  </el-row>

  <el-row justify="center" style="margin-right: 5%; margin-left: 5%">
    <el-col
      :xs="24"
      :sm="12"
      :md="12"
      :lg="12"
      :xl="12"
      style="display: flex; justify-content: center"
    >
      <div class="double-swiper">
        <div class="double-swiper-inner">
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
            style="margin-bottom: 4px"
          >
            <swiper-slide
              v-for="(item, index) in firstCrossGenImages"
              class="slide, slide_left"
              :key="index"
            >
              <div class="image-caption-wrapper">
                <el-image
                  :src="item.src"
                  class="responsive-image"
                  fit="contain"
                />
                <div class="caption">{{ item.caption }}</div>
              </div>
            </swiper-slide>
          </swiper>
        </div>
        <swiper
          ref="cross_swiper2"
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
          @swiper="onCrossLeftSlideInit"
          @slideChange="onCrossLeftSlideChange"
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
              <el-image
                :src="item.src"
                class="responsive-image"
                fit="contain"
              />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>
    <el-col :xs="24" :sm="12" :md="12" :lg="12" :xl="12">
      <div class="right-swiper">
        <span class="label">Manipulation</span>
        <swiper
          ref="cross_right_swiper"
          :loop="true"
          :slidesPerView="1"
          :modules="modules"
          :navigation="{
            hideOnClick: true,
          }"
          @swiper="onCrossRightSlideInit"
          @slideChange="onCrossRightSlideChange"
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
        >
          <swiper-slide
            v-for="item in cross_manipulation_image_paths"
            class="slide, slide_right"
            :key="item"
          >
            <div class="image-caption-wrapper">
              <el-image
                :src="item.src"
                class="responsive-image"
                fit="contain"
              />
              <div class="caption">{{ item.caption }}</div>
            </div>
          </swiper-slide>
        </swiper>
      </div>
    </el-col>
  </el-row>
  <!-- <el-row justify="center" style="margin-right: 5%; margin-left: 5%">
    <el-col :xs="6" :sm="6" :md="6" :lg="6" :xl="6" class="bottom-caption-left"
      ><div class="caption">{{ second_line[0] }}</div>
    </el-col>

    <el-col :xs="6" :sm="6" :md="6" :lg="6" :xl="6" class="bottom-caption-right"
      ><div class="caption">{{ second_line[1] }}</div>
    </el-col>
  </el-row> -->
</template>

<style>
.swiper {
  --swiper-theme-color: white;
  position: relative;
  max-width: 100%;
  max-width: 100%;
}

.slide_left,
.slide_right {
  justify-content: center;
}

/* .swiper-slide {
  display: flex;
  align-items: center;
  min-width: 30%;
} */

.double-swiper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 30%;
  max-width: 100%;
  /* margin-left: 15%; */
  /* margin-right: 10px; */
  align-items: center;
}
.double-swiper-inner {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  width: 100%;
}
.right-swiper {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  min-height: 30%;
  max-width: 100%;
  /* margin-right: 15%;
  margin-left: 10px; */
  align-items: center;
}

.image-caption-wrapper {
  display: flex;
  flex-direction: column;
  align-items: center;
}

.slide img {
  width: 100%;
  height: 100%;
  border-radius: 8px;
  display: block;
}
.responsive-image {
  width: 80%; /* 撑满容器宽度（即 80% 屏幕） */
  height: auto; /* 自动保持图片比例 */
  display: block; /* 去除底部空白 */
}

.caption {
  margin-top: 2px;
  margin-bottom: 3px;

  font-size: clamp(10px, 0.9vw, 120px);
  font-family: "Gill Sans", sans-serif;
  font-style: italic;
  color: #333;
  text-align: center;
}

/* .swiper-generation {
  width: 100%;
} */
.section-title {
  margin-top: 20px;
}
.section-title-h1 {
  font-size: clamp(20px, 1.4vw, 150px);
}
.swiper-button-prev,
.swiper-button-next {
  color: white;
}

/* 控制按钮位置 */
.swiper-button-prev {
  /* left: 25px;  */
  /* top: 45%; */
  display: none !important;
}

.swiper-button-next {
  /* right: 25px; */
  /* top: 45%; */
  display: none !important;
}
.label {
  color: #7e8481;
  font-family: "MyFont", Verdana, sans-serif;
  display: block; /* span 默认是 inline，改成 block 才能使用 text-align */
  text-align: center;
  margin-top: 5px; /* 可选 */
  margin-bottom: 10px;
  font-size: clamp(12px, 1vw, 120px);
}

.swiper-pagination {
  margin-top: 14px;
  position: relative;
  display: none !important;
}
.el-image__inner {
  width: 100%;
}

.double-swiper .swiper-pagination {
  /* margin-top: 14px;  */
  /* position: relative; */
  display: none !important;
}
.bottom-caption-left,
.bottom-caption-right {
  display: block;
  /* float: right; */
  /* flex-direction: column; */
  /* height: 95%; */
  /* height: 350px; */
  align-items: center;
  object-fit: contain;
}
.bottom-caption-left {
  margin-left: 25%;
}
.bottom-caption-right {
  margin-right: 25%;
}
</style>
