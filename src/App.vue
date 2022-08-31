<!--
 * @ Author: lj
 * @ Create Time: 2022-08-29 21:05:39
 * @ Modified by: 
 * @ Modified time: 2022-08-30 14:37:02
 * @ Description: 根组件
 -->

<template>
  <div id="app">
    <div style="font-weight: 600">Vue2公共组件整理</div>
    <el-menu
      :default-active="activeIndex"
      class="el-menu-demo"
      mode="horizontal"
      @select="handleSelect"
    >
      <el-menu-item index="1">饼图</el-menu-item>
      <el-menu-item index="2">折线图</el-menu-item>
      <el-menu-item index="3">柱状图</el-menu-item>
      <!-- <el-menu-item index="4">日期选择</el-menu-item> -->
      <el-menu-item index="99999">待定</el-menu-item>
    </el-menu>
    <Pieecharts v-if="isShow == 'pie'" />
    <Lineecharts v-else-if="isShow == 'line'" />
    <Barecharts v-else-if="isShow == 'bar'" />
    <DateSelection v-else-if="isShow == 'date'" />
    <kong v-else="isShow == 'kong'" />
    <!-- <router-view></router-view> -->
  </div>
</template>

<script>
import Pieecharts from "@/views/pie-echarts.vue";
import Lineecharts from "@/views/line-echarts.vue";
import Barecharts from "@/views/bar-echarts.vue";
// import DateSelection from "@/views/date-selection.vue";
import kong from "@/views/404.vue";

export default {
  name: "App",
  components: {
    Pieecharts,
    Lineecharts,
    Barecharts,
    // DateSelection,
    kong,
  },
  data() {
    return {
      activeIndex: "1",
      isShow: "pie",
    };
  },
  methods: {
    handleSelect(key, keyPath) {
      console.log(key, keyPath);
      if (key == 1) {
        this.isShow = "pie";
      } else if (key == 2) {
        this.isShow = "line";
      } else if (key == 3) {
        this.isShow = "bar";
      } else if (key == 4) {
        this.isShow = "date";
      } else {
        this.isShow = "kong";
      }
    },
  },
};
</script>

<style scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin: 0 auto;
}
.el-menu-demo {
  margin-bottom: 20px;
}
</style>
