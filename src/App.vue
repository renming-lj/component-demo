<!--
 * @ Author: lj
 * @ Create Time: 2022-08-29 21:05:39
 * @ Modified by: 
 * @ Modified time: 2022-08-31 16:29:27
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
      <el-menu-item index="4">搜索区域</el-menu-item>
      <el-menu-item index="5">纯数字输入框</el-menu-item>
      <el-menu-item index="6">分页组件</el-menu-item>
      <el-menu-item index="99999">待定</el-menu-item>
    </el-menu>
    <Pieecharts v-if="isShow == 'pie'" />
    <Lineecharts v-else-if="isShow == 'line'" />
    <Barecharts v-else-if="isShow == 'bar'" />
    <FormPlus v-else-if="isShow == 'form'" />
    <InputNumber v-else-if="isShow == 'number'" />
    <Pagination v-else-if="isShow == 'paging'" />
    <empty v-else-if="isShow == 'empty'" />
  </div>
</template>

<script>
import Pieecharts from "@/views/pie-echarts.vue";
import Lineecharts from "@/views/line-echarts.vue";
import Barecharts from "@/views/bar-echarts.vue";
import FormPlus from "@/views/form-plus.vue";
import InputNumber from "@/views/input-number.vue";
import Pagination from "@/views/pagination.vue";
import empty from "@/views/404.vue";

export default {
  name: "App",
  components: {
    Pieecharts,
    Lineecharts,
    Barecharts,
    FormPlus,
    InputNumber,
    Pagination,
    empty,
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
        this.isShow = "form";
      } else if (key == 5) {
        this.isShow = "number";
      } else if (key == 6) {
        this.isShow = "paging";
      } else {
        this.isShow = "empty";
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
