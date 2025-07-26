<script setup>
import abstract from '../mds/abstract.mdx';
</script>

<template>
  <div>
    <el-divider />

    <el-row justify="center">
        <el-col :xs="24" :sm="20" :md="16" :lg="12" :xl="12">
            <abstract />
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