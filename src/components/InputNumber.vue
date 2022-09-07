<!--
 * @ Author: lj
 * @ Create Time: 2022-08-30 00:04:55
 * @ Modified by:
 * @ Modified time: 2022-08-30 00:26:34
 * @ Description: 纯数字输入框组件封装
 -->

<template>
  <el-input-number id="InputNumber"
                   style="width: 100%"
                   v-model="insideValue"
                   v-bind="$attrs"
                   :controls="controls"
                   placeholder="请输入数字"
                   v-on="$listeners"
                   clearable="true"/>
</template>

<script>
export default {
  // 让父组件 v-model 传参
  model: {
    prop: 'numberValue',
    event: 'change',
  },
  props: {
    numberValue: {
      type: [Number, String],
      default: undefined,
    },
    // 默认不显示控制按钮，这个可以根据实际情况做调整
    controls: {
      type: Boolean,
      default: false,
    },
  },
  data() {
    return {
      insideValue: undefined,
    };
  },
  watch: {
    numberValue(newVlalue) {
      // 若传入一个数字就显示。为空则不显示
      if (typeof newVlalue === 'number') {
        this.insideValue = newVlalue;
      } else this.insideValue = undefined;
    },
  },
};
</script>

<style scoped>
/deep/ .el-input__inner {
  text-align: left !important;
}
</style>