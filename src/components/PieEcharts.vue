<!--
 * @ Author: lj
 * @ Create Time: 2022-08-29 21:20:18
 * @ Modified by: 
 * @ Modified time: 2022-08-30 00:26:48
 * @ Description: echarts饼图组件
 -->

<template>
  <div>
    <div :ref="piechartRef" class="piechart" :class="className"></div>
  </div>
</template>

<script>
import * as echarts from "echarts";

export default {
  name: "Piechart",
  props: {
    options: { type: Object, default: {} },
    piechartRef: { type: String, default: "piechart" },
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
      let myCharts = echarts.init(this.$refs[this.piechartRef]);
      myCharts.setOption(val);
      window.addEventListener("resize", function () {
        myCharts.resize();
      });
    },
  },
};
</script>

<style scoped>
.piechart {
  width: calc(100vw - 260px - 40px - 40px);
  height: 600px;
}
</style>
