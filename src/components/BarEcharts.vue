<!--
 * @ Author: lj
 * @ Create Time: 2022-08-30 11:43:27
 * @ Modified by: 
 * @ Modified time: 2022-08-30 11:44:50
 * @ Description: echarts柱状图组件
 -->

<template>
  <div>
    <div :ref="barchartRef" class="echartbox" :class="className"></div>
  </div>
</template>

<script>
import * as echarts from "echarts";

export default {
  name: "Barchart",
  props: {
    options: { type: Object, default: {} },
    barchartRef: { type: String, default: "barchart" },
    className: { type: String, default: "" },
  },
  data() {
    return {};
  },
  created() {},
  watch: {
    options: {
      handler: function (newVal) {
        this.drawBar(newVal);
      },
      deep: true,
    },
  },
  mounted() {
    this.drawBar(this.options);
  },
  methods: {
    drawBar(val) {
      let myCharts = echarts.init(this.$refs[this.barchartRef]);
      myCharts.setOption(val);
      window.addEventListener("resize", function () {
        myCharts.resize();
      });
    },
  },
};
</script>

<style scoped>
.echartbox {
  width: calc(100vw - 260px - 40px - 40px);
  height: 600px;
}
</style>
