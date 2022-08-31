<!--
 * @ Author: lj
 * @ Create Time: 2022-08-29 21:08:56
 * @ Modified by: 
 * @ Modified time: 2022-08-30 00:51:45
 * @ Description: 饼图组件使用
 -->

<template>
  <div>
    <PieEchart :piechartRef="piechartRef" :options="options"></PieEchart>
  </div>
</template>

<script>
import PieEchart from "@/components/PieEcharts.vue";
export default {
  components: {
    PieEchart,
  },
  data() {
    return {
      options: {
        title: [
          {
            text: "可售面积占比",
            x: "20%",
            y: "25%",
            textStyle: {
              fontSize: 16,
            },
          },
          {
            text: "已售面积占比",
            x: "70%",
            y: "25%",
            textStyle: {
              fontSize: 16,
            },
          },
        ],
        color: ["#4c98dc", "#ea717a", "#6dcbb3"],
        legend: {
          orient: "vertical",
          x: "right",
        },
        tooltip: {
          trigger: "item",
          formatter: "{b} :  ({d}%)",
        },
        dataset: {
          source: [
            ["group", "可售面积占比", "已售面积占比"],
            ["普通住宅", 57.02, 48.55],
            ["非普通住宅", 27.09, 16.03],
            ["其他类型房产", 15.89, 35.42],
          ],
        },
        series: [
          {
            type: "pie",
            radius: [60, 90],
            center: ["25%", "50%"],
            encode: {
              itemName: "group",
              value: "可售面积占比",
            },
            label: {
              show: true,
              formatter: "{b}: {d}%",
            },
          },
          {
            type: "pie",
            radius: [60, 90],
            center: ["75%", "50%"],
            encode: {
              itemName: "group",
              value: "已售面积占比",
            },
            label: {
              show: true,
              formatter: "{b}: {d}%",
            },
          },
        ],
      },
      piechartRef: "piechart",
    };
  },
};
</script>

<style></style>
