<!--
 * @ Author: lj
 * @ Create Time: 2022-08-30 00:04:55
 * @ Modified by: 
 * @ Modified time: 2022-08-30 00:26:34
 * @ Description: echarts折线图组件
 -->

<template>
  <div>
    <div :ref="linechartRef" class="echartbox" :class="className"></div>
  </div>
</template>

<script>
import * as echarts from "echarts";

export default {
  name: "LineChart",
  props: {
    options: { type: Object, default: {} },
    linechartRef: { type: String, default: "linechart" },
    className: { type: String, default: "" },
  },
  data() {
    return {};
  },
  created() {},
  watch: {
    options: {
      handler: function (newVal) {
        this.drawLine(newVal);
      },
      deep: true,
    },
  },
  mounted() {
    this.drawLine(this.options);
  },
  methods: {
    drawLine(val) {
      let myCharts = echarts.init(this.$refs[this.linechartRef]);
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
