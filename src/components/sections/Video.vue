<script setup>
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <!-- <h1 class="section-title">Teasor</h1> -->
    </el-row>
    <!-- <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12"> -->
        <!-- local -->
        <!-- <el-container class="video-container">
          <video controls muted preload playsinline>
            <source src="/video/video.mp4" type="video/mp4">
          </video>
        </el-container> -->
        <!-- <el-container class="video-container">
          <el-image src="./carousel/teaser_rotation_gif.gif" fit="contain" />
        </el-container>
      </el-col>
    </el-row> -->

    <!-- <el-row justify="center">
      <h1 class="section-title">Pipeline</h1>
    </el-row> -->

    <el-row justify="center">
      <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
        <el-container class="video-container">
          <el-image src="./carousel/Banner.png" fit="contain" />
        </el-container>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.video-container {
  margin: 20px 0px 0px 0px;
}

iframe,
video {
  aspect-ratio: 16 / 9;
  width: 100%;
}

.section-title {
  margin-top: 40px;
  /* 添加标题的上边距 */
}
</style>