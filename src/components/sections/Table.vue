<script lang="ts" setup>
// 表格数据
const table_img = [
  "./table/Exp-BenchRank.png",
  "./table/Exp-SR-E2E.png",
  "./table/Exp-AgileX-SR-E2E.png",
  "./table/Exp-Franka-SR-E2E.png",
];
const tableData = [
  {
    model: "Model A",
    params: "10 B",
    value_a: "123",
    value_b: "321",
  },
  {
    model: "Model B",
    params: "30 B",
    value_a: "456",
    value_b: "654",
  },
  {
    model: "Model C",
    params: "20 B",
    value_a: "789",
    value_b: "987",
  },
  {
    model: "Model D",
    params: "5 B",
    value_a: "100",
    value_b: "200",
  },
];
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
      <h1 class="section-title">Experimental Results</h1>
    </el-row>

    <!-- 数据表格 -->
    <el-row justify="center">
      <el-col :xs="16" :sm="16" :md="12" :lg="12" :xl="12">
        <el-card class="card">
          <el-tabs class="demo-tabs" model-value="Method B">
            <!-- <el-tab-pane label="Video Benchmark" name="Video Benchmark">
              <div class="image-wrapper">
                <el-image
                  style="width: 100%; height: 100%"
                  :src="table_img[0]"
                  fit="contain"
                ></el-image>
              </div>
            </el-tab-pane> -->

            <el-tab-pane
              label="Manipulation Performance on Agibot G1"
              name="Method B"
            >
              <div class="image-wrapper">
                <el-image
                  style="width: 100%; height: 100%"
                  :src="table_img[1]"
                  fit="contain"
                ></el-image>
              </div>
            </el-tab-pane>

            <el-tab-pane
              label="Manipulation Performance on AgileX"
              name="Method C"
            >
              <div class="image-wrapper">
                <el-image
                  style="width: 100%; height: 100%"
                  :src="table_img[2]"
                  fit="contain"
                ></el-image>
              </div>
            </el-tab-pane>

            <el-tab-pane
              label="Manipulation Performance on Dual Franka"
              name="Method D"
            >
              <div class="image-wrapper">
                <el-image
                  style="width: 100%; height: 100%"
                  :src="table_img[3]"
                  fit="contain"
                ></el-image>
              </div>

              <!-- <el-table 
                            :data="tableData"
                            :default-sort="{ prop: 'value_b', order: 'descending' }"
                            scrollbar-always-on
                        >
                            <el-table-column prop="model" label="Model" width="100" sortable/>
                            <el-table-column prop="params" label="#Params" min-width="120" sortable/>
                            <el-table-column prop="value_a" label="Value A" min-width="120" sortable/>
                            <el-table-column prop="value_b" label="Value B" min-width="120" sortable/>
                        </el-table> -->
            </el-tab-pane>
          </el-tabs>
        </el-card>
      </el-col>
    </el-row>
  </div>
</template>

<style scoped>
.card {
  margin-top: 20px;
}
.demo-tabs {
  max-height: 350px;
}
.image-wrapper {
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
