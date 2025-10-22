<script setup>
import { ref } from "vue";

const secTrajVideoPaths = [
  [
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_up/video_with_traj_11.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_forward-back/video_with_traj_7.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/rightarm_forward-closegripper-back/video_with_traj_5.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/botharm_random/video_with_traj_13.mp4",
  ],
  [
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_up/video_with_traj_23.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_forward-back/video_with_traj_17.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/rightarm_forward-closegripper-back/video_with_traj_15.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/botharm_random/video_with_traj_25.mp4",
  ],
  [
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_up/video_with_traj_33.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_forward-back/video_with_traj_29.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/rightarm_forward-closegripper-back/video_with_traj_27.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/botharm_random/video_with_traj_35.mp4",
  ],
  [
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_up/video_with_traj_45.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/leftarm_forward-back/video_with_traj_40.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/rightarm_forward-closegripper-back/video_with_traj_38.mp4",
    "./image_selector/demo_collection/mannual_trajs_split/botharm_random/video_with_traj_37.mp4",
  ],
];
const failed_and_success_videos = [
  "./image_selector/demo_collection/fail_success_trajs/fail_episode/video.mp4",
  "./image_selector/demo_collection/fail_success_trajs/success_episode/video.mp4",
];
const ori_traj_videos = [
  "./image_selector/demo_collection/ori_trajs/traj_1/video.mp4",
  "./image_selector/demo_collection/ori_trajs/traj_2/video.mp4",
];

// 当前每个 section 播放的视频
const currentVideos = ref(secTrajVideoPaths.map((section) => section[0]));
const selectedTarget = ref(Array(secTrajVideoPaths.length).fill("left")); // 默认 target
const selectedAction = ref(Array(secTrajVideoPaths.length).fill("up")); // 默认 action

// Target -> Action 映射
const targetActionsMap = {
  left: ["up", "forward-back"],
  right: ["forward-closegripper-back"],
  both: ["random"],
};

// Target + Action -> secTrajVideoPaths 索引映射
const actionIndexMap = {
  left: { up: 0, "forward-back": 1 },
  right: { "forward-closegripper-back": 2 },
  both: { random: 3 },
};

const handleTargetChange = (sectionIndex, target) => {
  selectedTarget.value[sectionIndex] = target;
  // 默认选择第一个 action
  selectedAction.value[sectionIndex] = targetActionsMap[target][0];
  const action = selectedAction.value[sectionIndex];
  const videoIndex = actionIndexMap[target][action];
  currentVideos.value[sectionIndex] =
    secTrajVideoPaths[sectionIndex][videoIndex];
};

const handleActionChange = (sectionIndex, action) => {
  selectedAction.value[sectionIndex] = action;
  const target = selectedTarget.value[sectionIndex];
  const videoIndex = actionIndexMap[target][action];
  currentVideos.value[sectionIndex] =
    secTrajVideoPaths[sectionIndex][videoIndex];
};
</script>

<template>
  <div>
    <el-divider></el-divider>
    <el-row justify="center" style="margin-top: 20px; margin-bottom: 20px">
      <h1 class="secions-name">GE-Sim</h1>
    </el-row>

    <!-- 2x2 布局 -->
    <el-row :gutter="1" justify="center">
      <el-col v-for="(section, i) in secTrajVideoPaths" :key="i" :span="11">
        <div class="section-card">
          <h3 class="section-title">Scene {{ String.fromCharCode(65 + i) }}</h3>

          <div class="button-line">
            <div class="button-group">
              <div class="line-label">Target:</div>
              <el-button
                v-for="target in ['left', 'right', 'both']"
                :key="target"
                size="medium"
                type="primary"
                class="custom-btn"
                :plain="selectedTarget[i] !== target"
                @click="handleTargetChange(i, target)"
              >
                {{ target }}
              </el-button>
            </div>
          </div>

          <!-- 第二行 Action -->
          <div class="button-line">
            <div class="button-group">
              <span class="line-label">Action:</span>
              <el-button
                v-for="action in targetActionsMap[selectedTarget[i]]"
                :key="action"
                size="medium"
                type="success"
                class="custom-btn"
                round
                :plain="selectedAction[i] !== action"
                @click="handleActionChange(i, action)"
              >
                {{ action }}
              </el-button>
            </div>
          </div>

          <!-- 视频展示 -->
          <video
            :src="currentVideos[i]"
            class="demo-video"
            controls
            autoplay
            muted
            loop
          ></video>
        </div>
      </el-col>
    </el-row>

    <el-row
      justify="center"
      style="margin-top: 2%; margin-right: 3%; margin-left: 3%"
    >
      <el-col
        :xs="24"
        :sm="12"
        :md="12"
        :lg="12"
        :xl="12"
        style="display: flex; justify-content: center"
      >
        <div class="section-card">
          <div class="left_video">
            <span class="label">Failed Case</span>
            <video
              :src="failed_and_success_videos[0]"
              class="demo-video"
              controls
              autoplay
              muted
              loop
            ></video>
          </div>
        </div>
      </el-col>
      <el-col
        :xs="24"
        :sm="12"
        :md="12"
        :lg="12"
        :xl="12"
        style="display: flex; justify-content: center"
      >
        <div class="section-card">
          <div class="right_video">
            <span class="label">Success Case</span>
            <video
              :src="failed_and_success_videos[1]"
              class="demo-video"
              controls
              autoplay
              muted
              loop
            ></video>
          </div>
        </div>
      </el-col>
    </el-row>
    <el-row justify="center" class="subsection-name">
      <span>Original Trajectory</span>
    </el-row>
    <el-row
      justify="center"
      style="margin-top: 2%; margin-right: 3%; margin-left: 3%"
    >
      <el-col
        :xs="24"
        :sm="12"
        :md="12"
        :lg="12"
        :xl="12"
        style="display: flex; justify-content: center"
      >
        <div class="left_video">
          <video
            :src="ori_traj_videos[0]"
            class="demo-video"
            controls
            autoplay
            muted
            loop
          ></video>
        </div>
      </el-col>
      <el-col
        :xs="24"
        :sm="12"
        :md="12"
        :lg="12"
        :xl="12"
        style="display: flex; justify-content: center"
      >
        <div class="right_video">
          <video
            :src="ori_traj_videos[1]"
            class="demo-video"
            controls
            autoplay
            muted
            loop
          ></video>
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.section-card {
  border: 1px solid #ddd;
  border-radius: 10px;
  padding: 15px;
  margin-bottom: 20px;
  text-align: center;
  box-shadow: 0 2px 8px rgba(0, 0, 0, 0.05);
  max-width: 80%;
  margin: 1% auto;
}
.left_video {
  display: flex;
  flex-direction: column;
  align-items: center;
  /* max-width: 90%; */
}
.right_video {
  display: flex;
  flex-direction: column;
  align-items: center;
  /* max-width: 90%; */
}
.secions-name {
  font-size: clamp(20px, 1.4vw, 150px);
  color: #222;
  margin-bottom: 10px;
}
.subsection-name {
  font-family: "MyFont", Verdana, sans-serif;
  font-size: clamp(16px, 1.2vw, 120px);
  color: #444;
  /* margin-bottom: 10px; */
  margin-top: 2%;
}

.section-title {
  font-size: clamp(15px, 1.1vw, 100px);
  margin-top: 3px;
  margin-bottom: 10px;
  color: #333;
}

.line-label {
  font-family: "MyFont", Verdana, sans-serif;
  font-size: 14px;
  color: #666;
  font-weight: bold;
  display: flex;
  margin-right: 10px;
  align-items: center;
  height: 100%;
  line-height: 32px;
}

.button-group {
  display: flex;
  flex-wrap: wrap;
  gap: 8px;
  margin-left: 3%;
  margin-bottom: 10px;
  justify-content: flex-start;
}
.custom-btn {
  font-size: clamp(12px, 1.05vw, 120px);
}
.demo-video {
  max-width: 95%;
  object-fit: contain;
  border-radius: 8px;
}
</style>
