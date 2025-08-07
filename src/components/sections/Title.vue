<script lang="ts" setup>
import { ElIcon } from "element-plus";
import {
  Document,
  Files,
  MagicStick,
  Picture,
  DataAnalysis,
  Film,
} from "@element-plus/icons-vue";

const logo = "./AgiBot.jpg";

const title = "Genie Envisioner";

const title_color = "#53abe1";

const title_supp = "A Unified World Foundation Model for Robotic Manipulation";

const title_supp_color = "#75579b";

const btn_color = "#444444";

const authors = [
  { name: "Yue Liao", address_flag: "*" },
  { name: "Pengfei Zhou", address_flag: "*" },
  { name: "Siyuan Huang", address_flag: "*" },
  { name: "Donglin Yang", address_flag: "" },
  { name: "Shengcong Chen", address_flag: "" },
  { name: "Yuxin Jiang", address_flag: "" },
  { name: "Yue Hu", address_flag: "" },
  { name: "Jingbin Cai", address_flag: "" },
  { name: "Si Liu", address_flag: "" },
  { name: "Jianlan Luo", address_flag: "" },
  { name: "Liliang Chen", address_flag: "†" },
  { name: "Shuicheng Yan", address_flag: "◆" },
  { name: "Maoqing Yao", address_flag: "◆" },
  { name: "Guanghui Ren", address_flag: "†◆" },
];

// 地址清单（包含地址名称、头像、主页、地址序号）
const addresses = [
  {
    // address_flag: "1",
    name: "AgiBot",
    homepage: "https://www.agibot.com/",
  },
  {
    // address_flag: "2",
    name: "NUS LV-Lab",
    // homepage: "https://"
  },
  {
    // address_flag: "3",
    name: "BUAA",
  },
];

const con_and_corresponding_author =
  "* Equal Contribution.   ◆ Corresponding Author.   † Project Leader.";

// 提供引导资料链接
const buttons = [
  {
    disabled: false,
    name: "Paper",
    link: "https://arxiv.org/abs/25",
    component: Document,
  },
  {
    disabled: false,
    name: "Code",
    link: "https://github.com/AgibotTech/Genie-Envisioner",
    component: Files,
  },
];
</script>

<template>
  <div>
    <!-- 文章logo -->
    <!-- <el-row v-if="logo" justify="center">
      <el-image :src="logo" class="logo" fit="cover" />
    </el-row> -->

    <!-- 文章标题 -->
    <el-row justify="center">
      <el-col :span="20" style="text-align: center">
        <h1 class="paper-title" style="margin-bottom: 1%">
          <span v-if="title" :style="{ color: title_color }"> {{ title }}</span>
        </h1>
        <h3 style="margin-top: 0">
          <span v-if="title_supp" :style="{ color: title_supp_color }">
            {{ title_supp }}</span
          >
        </h3>
      </el-col>
    </el-row>

    <!-- 作者名单 -->

    <el-row justify="center" style="max-width: 55%; margin: 0 auto">
      <a :href="author.homepage" v-for="author in authors">
        <el-button class="title-button" type="primary" text>
          <el-avatar v-if="author.icon" :size="40" :src="author.icon" />
          <span class="author">
            {{ author.name
            }}<sup v-if="author.address_flag" class="name_sup">{{
              author.address_flag
            }}</sup>
          </span>
        </el-button>
      </a>
    </el-row>

    <!-- 地址名单 -->

    <el-row justify="center">
      <a :href="address.homepage" v-for="address in addresses">
        <el-button class="title-button, address-button" type="primary" text>
          <el-avatar v-if="address.icon" :size="40" :src="address.icon" />
          <span class="address">
            <sup v-if="address.address_flag" class="address_sup">{{
              address.address_flag
            }}</sup
            >{{ address.name }}
          </span>
        </el-button>
      </a>
    </el-row>

    <!-- 共一和通讯提示内容 -->
    <el-row justify="center" class="con-cor">
      {{ con_and_corresponding_author }}
    </el-row>

    <!-- 强调内容 -->
    <el-row justify="center" class="emphasis" v-for="emphasis in emphases">
      {{ emphasis }}
    </el-row>

    <!-- 提供引导按钮 -->
    <el-row justify="center" style="margin-bottom: 20px">
      <el-col :span="20">
        <el-row justify="center">
          <a :href="button.link" v-for="button in buttons">
            <el-button
              class="guidance-button"
              size="default"
              :color="btn_color"
              :disabled="button.disabled"
              round
            >
              <el-icon :size="18">
                <component :is="button.component" />
              </el-icon>
              <span class="btn-text">{{ button.name }}</span>
            </el-button>
          </a>
        </el-row>
        <el-row justify="center">
          <div class="progress-wrapper">
            <div class="progress-bar">
              <div class="progress-fill" :style="{ width: '80%' }">
                <div class="progress-text" style="text-align: center">
                  Coming Soon
                </div>
              </div>
            </div>
          </div>
        </el-row>
      </el-col>
    </el-row>

    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="16" :xl="16">
        <el-container class="video-container">
          <video
            controls
            muted
            preload
            playsinline
            style="
              max-width: 90%;
              height: auto;
              display: block;
              margin: 0 auto;
              border-radius: 8px;
            "
          >
            <source src="/video/agibot-genie-intro-v1.mp4" type="video/mp4" />
          </video>
        </el-container>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.paper-title {
  font-family: "MyFont", Verdana, sans-serif;
  letter-spacing: 2px;
  font-size: clamp(10px, 10vw, 50px);
  margin: 32px;
  text-align: center;
  margin-top: 2%;
  word-break: break-word;
  white-space: normal;
}

/* 姓名和地址按钮 */
.title-button {
  /* margin: 10px 3px; */
  padding: 1px 5px;
}

/* 姓名和地址按钮光标悬浮 */
.title-button:hover {
  margin: 2px 3px;
}

/* 引导材料按钮 */
.guidance-button {
  margin: 8px 5px;
  box-shadow: #d8d8d8 1px 1px 1px 1px;
}

/* 姓名属性 */
.author {
  font-size: clamp(10px, 8vw, 20px);
  margin-left: 3px;
  color: rgb(63, 59, 77);
}

/* 姓名上标属性 */
.name_sup {
  color: #000000;
  margin-left: 3px;
}

/* 地址属性 */
.address {
  font-size: 18px;
  color: rgb(0, 0, 0);
}

/* 地址上标属性 */
.address_sup {
  color: #606266;
  margin-right: 1px;
}

/* 头像属性 */
.el-avatar {
  margin-right: 6px;
  box-shadow: #b7b7b7 0px 0px 3px 1px;
}

/* 共一和通讯文字属性 */
.con-cor {
  font-family: Arial;
  font-size: 14px;
  margin: 10px 0px 5px 0px;
  text-align: center;
}

/* 强调信息属性 */
.emphasis {
  color: chocolate;
  font-weight: bold;
  margin: 8px;
  font-size: 22px;
  text-align: center;
}

/* 引导材料按钮文字属性 */
.btn-text {
  font-size: 18px;
  color: #ffffff;
}

.el-alert {
  margin: 10px 0 0;
}

.el-alert:first-child {
  margin: 0;
}

.logo {
  width: 20%;
  height: 15%;
  /* border-radius: 20%; */
  /* box-shadow: #ced3dc 0px 0px 3px 2px; */
  margin-top: 40px;
}

/* 手机端链接样式处理 */
a:-webkit-any-link {
  text-decoration: none;
}

/* 取消鼠标焦点悬浮在链接上的颜色装饰 */
a:hover {
  color: inherit;
  border-bottom: none;
}

/* 链接装饰，取消下划线和链接颜色 */
a {
  text-decoration: None;
  color: inherit;
}

.progress-wrapper {
  width: 100%;
  max-width: 200px;
  margin: 0 auto;
}

.progress-bar {
  width: 100%;
  height: 20px;
  background-color: #eee;
  border-radius: 5px;
  overflow: hidden;
  position: relative;
}

.progress-fill {
  height: 100%;
  background: linear-gradient(120deg, #a1c4fd 0%, #c2e9fb 100%);
  animation: fillLoop 5s ease-in-out infinite;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
  color: white;
  font-size: 15px;
  transition: width 0.3s ease;
}

/* 动画从 0% 到 80%，再回到 0% */
@keyframes fillLoop {
  0% {
    width: 10%;
  }
  50% {
    width: 60%;
  }
  100% {
    width: 80%;
  }
}

.progress-text {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 20px;
  font-size: 12px;
  text-align: center;
  /* margin-bottom: 5px; */
  font-family: "MyFont", Verdana, sans-serif;
  color: #333;
  position: absolute;
  left: 91%;
  transform: translateX(-50%);
  white-space: nowrap;
}
</style>
// 首页的视频 更新分辨率 视频添加instr 体现记忆 // 左右margin 减少 //
作者行间距、间距 & 单位 // // 对应关系 prompt: 把盒子叠好
把黄色圆形糖果/白色方形糖果放进盒子里，盖上盖子，并盖上对应的章 // （黄色
蓝章）、 （白色 红章） // 视频开头 + 介绍 （跨本体、软体夹具、memory） //
第一段完整 + 分屏 // agibot g1 daoshui // 动图大些
