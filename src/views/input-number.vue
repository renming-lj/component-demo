<!--
 * @ Author: lj
 * @ Create Time: 2022-08-30 00:04:55
 * @ Modified by:
 * @ Modified time: 2022-08-30 00:26:34
 * @ Description: 纯数字输入框组件使用
 -->

<template>
  <InputNumber v-model="value"
               style="width: 200px" :controls="false"/>
</template>

<script>
import InputNumber from '@/components/InputNumber.vue';

export default {
  components: {
    InputNumber,
  },
  data() {
    return {
      value: null,
    };
  },
};
</script>