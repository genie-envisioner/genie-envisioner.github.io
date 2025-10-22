<script>
export default {
  data() {
    return {
      bibtex: [
        "@article{ge2025,",
        "    title={Genie Envisioner: A Unified World Foundation Platform for Robotic Manipulation},",
        "    author={Yue Liao and Pengfei Zhou and Siyuan Huang and Donglin Yang and Shengcong Chen and Yuxin Jiang and Yue Hu and Jingbin Cai and Si Liu and Jianlan Luo and Liliang Chen and Shuicheng Yan and Maoqing Yao and Guanghui Ren},",
        "    journal={arXiv preprint arXiv:2508.05635},",
        "    year={2025}",
        "}",
      ],
    };
  },
  methods: {
    copyVal() {
      let oInput = document.createElement("textarea");
      let text = document.getElementById("bibtex").innerText;
      oInput.value = text;
      document.body.appendChild(oInput);
      oInput.select();
      document.execCommand("Copy");
      this.$message.success("Copy Successfully");
      oInput.remove();
    },
  },
};
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title">BibTeX</h1>
    </el-row>

    <el-row justify="center">
      <el-col
        class="bibtex"
        :xs="24"
        :sm="24"
        :md="20"
        :lg="20"
        :xl="16"
        @click="copyVal()"
      >
        <div
          style="
            text-align: center;
            color: var(--el-text-color-secondary);
            margin-top: 20px;
          "
        >
          🖱️ Click here to copy BibTex.
        </div>
        <el-row>
          <el-scrollbar style="margin: 0px 20px 5px 20px">
            <pre id="bibtex"><code v-for="b in bibtex">{{ b }}<br/></code></pre>
          </el-scrollbar>
        </el-row>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.scrollbar-flex-content {
  display: flex;
}

/* 卡片属性 */
.bibtex {
  margin: 20px 0px;
  padding-top: 5px;
  box-shadow: var(--el-box-shadow-light);
  border-radius: 10px;
}

/* 卡片悬浮 */
.bibtex:hover {
  box-shadow: var(--el-box-shadow);
}

/* 卡片点击 */
.bibtex:active {
  box-shadow: var(--el-box-shadow-lighter);
}

pre {
  border: none;
  border-radius: 0px;
  padding: 10px;
  background: none;
}

pre code {
  font-size: 18px;
  background: #ffffff;
}

.section-title {
  font-size: clamp(20px, 1.4vw, 150px);
}
</style>
