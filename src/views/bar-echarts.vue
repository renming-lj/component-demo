<!--
 * @ Author: lj
 * @ Create Time: 2022-08-30 11:45:06
 * @ Modified by: 
 * @ Modified time: 2022-08-30 11:50:04
 * @ Description: 柱状图组件使用
 -->

<template>
  <div>
    <BarEchart :barchartRef="barchartRef" :options="options"></BarEchart>
  </div>
</template>

<script>
import BarEchart from "@/components/BarEcharts.vue";
export default {
  components: {
    BarEchart,
  },
  data() {
    return {
      options: {
        tooltip: {
          trigger: "axis",
          axisPointer: {
            type: "shadow",
          },
        },
        legend: {
          data: ["生产量", "销量", "库存量"],
        },
        toolbox: {
          show: true,
          orient: "vertical",
          left: "right",
          top: "center",
          feature: {
            mark: { show: true },
            dataView: { show: true, readOnly: false },
            magicType: { show: true, type: ["line", "bar", "stack"] },
            restore: { show: true },
            saveAsImage: { show: true },
          },
        },
        xAxis: [
          {
            type: "category",
            axisTick: { show: false },
            data: [
              "period001",
              "period002",
              "period003",
              "period004",
              "period005",
            ],
          },
        ],
        yAxis: [
          {
            type: "value",
          },
        ],
        series: [
          {
            name: "生产量",
            type: "bar",
            barGap: 0,
            label: {
              show: true,
              position: "insideBottom",
              distance: 19,
              align: "left",
              verticalAlign: "middle",
              rotate: 90,
              formatter: "{c}  {name|{a}}",
              fontSize: 16,
              rich: {
                name: {},
              },
            },
            emphasis: {
              focus: "series",
            },
            data: [320, 332, 301, 334, 390],
          },
          {
            name: "销量",
            type: "bar",
            label: {
              show: true,
              position: "insideBottom",
              distance: 19,
              align: "left",
              verticalAlign: "middle",
              rotate: 90,
              formatter: "{c}  {name|{a}}",
              fontSize: 16,
              rich: {
                name: {},
              },
            },
            emphasis: {
              focus: "series",
            },
            data: [220, 182, 191, 234, 290],
          },
          {
            name: "库存量",
            type: "bar",
            label: {
              show: true,
              position: "insideBottom",
              distance: 19,
              align: "left",
              verticalAlign: "middle",
              rotate: 90,
              formatter: "{c}  {name|{a}}",
              fontSize: 16,
              rich: {
                name: {},
              },
            },
            emphasis: {
              focus: "series",
            },
            data: [150, 232, 201, 154, 190],
          },
        ],
      },
      barchartRef: "barchart",
    };
  },
};
</script>

<style></style>
