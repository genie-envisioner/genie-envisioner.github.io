<script setup>
import abstract from '../mds/abstract.mdx';
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <div style="textAlign: justify">
            <p style="font-size: 20px;">
            We introduce <strong style="color:#5DB3E6;">Genie Envisioner (GE)</strong>, a <span style="color:#5DB3E6;">unified world-model framework</span> that learns and evaluates robotic manipulation policies in a single generative loop. The core, <strong style="color:#5DB3E6;">GE-Base</strong>, is an instruction-conditioned, multi-view video diffusion model trained on over 1 million real-world episodes from the AgiBot-World-Beta corpus, capturing scene dynamics and robot-environment interactions in a structured latent space. <strong style="color:#5DB3E6;">GE-Act</strong>, built in parallel with the foundation model, incorporates a flow-matching action expert to map these latents to predict 54-step torque trajectories in 200 ms on commodity GPUs. It demonstrates strong task execution capabilities on the in-domain <strong>AgiBot G1</strong> platform, and generalizes to novel embodiments Franka and AgileX Cobot with only 1 hour of teleoperated demonstrations. <strong style="color:#5DB3E6;">GE-Sim</strong> provides a closed-loop, action-conditioned neural simulator capable of generating <strong>thousands of rollouts per hour</strong> for efficient evaluation and policy training. <strong style="color:#5DB3E6;">GE-Bench</strong> further complements GE with standardized metrics for visual fidelity, physical consistency, and instruction–action alignment. Together, these components form a practical and scalable foundation for general-purpose robotic manipulation.
            </p>
            </div>
            <div style="display: flex; justify-content: center; align-items: center; ">
              <el-image style="display: flex; justify-content: center; align-items: center; width: 90%; height: 90%;"
                src="./carousel/Banner.png"
                fit="contain"
              />
            </div>
        </el-col>
    </el-row>

  </div>
</template>

<style scoped>

</style>