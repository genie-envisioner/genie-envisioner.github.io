<script setup>
import abstract from "../mds/abstract.mdx";
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <el-col :xs="24" :sm="24" :md="16" :lg="16" :xl="16">
        <div style="textalign: justify">
          <p style="font-size: clamp(10px, 1.1vw, 40px); line-height: 1.6">
            We introduce
            <strong style="color: #5db3e6">Genie Envisioner (GE)</strong>, a
            <span style="color: #5db3e6"
              >unified world foundation platform</span
            >
            for robotic manipulation that integrates policy learning,
            evaluation, and simulation within a single video-generative
            framework. At its core,
            <strong style="color: #5db3e6">GE-Base</strong> is a large-scale,
            instruction-conditioned video diffusion model that captures the
            spatial, temporal, and semantic dynamics of real-world robotic
            interactions in a structured latent space. Built upon this
            foundation, <strong style="color: #5db3e6">GE-Act</strong> maps
            latent representations to executable action trajectories through a
            lightweight, flow-matching decoder, enabling precise and
            generalizable policy inference across diverse embodiments with
            minimal supervision. To support scalable evaluation and training,
            <strong style="color: #5db3e6">GE-Sim</strong> serves as an
            action-conditioned neural simulator, producing high-fidelity
            rollouts for closed-loop policy development. The platform is further
            equipped with <strong style="color: #5db3e6">EWMBench</strong>, a
            standardized benchmark suite measuring visual fidelity, physical
            consistency, and instruction-action alignment. Together, these
            components establish Genie Envisioner as a scalable and practical
            foundation for instruction-driven, general-purpose embodied
            intelligence.
          </p>
        </div>
        <div class="banner-image">
          <el-image
            style="
              display: flex;
              justify-content: center;
              align-items: center;
              width: 90%;
              height: 90%;
            "
            src="./carousel/Banner.png"
            fit="contain"
          />
        </div>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
/* @media (max-width: 1000px) {
} */
@media (max-width: 1000px) {
  .banner-image {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 auto;
    max-width: 80vw;
  }
}
@media (min-width: 1001px) {
  .banner-image {
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 0 auto;
    max-width: 60vw;
  }
}
</style>
