<!--
 * @ Author: lj
 * @ Create Time: 2022-08-29 21:08:56
 * @ Modified by:
 * @ Modified time: 2022-08-30 00:51:45
 * @ Description: 搜索框组件使用
 -->

<template>
  <div>
    <FormPlus :list="formList"
              @submitForm="searchPage"
              @resetForm="resetForm" />
    <div style="display: flex;justify-content: space-between;width: 74%;margin: 50px auto">
<!--      搜索数据收集：-->
      <div>编号：{{dataList.applyNumber}}</div>
      <div>名称：{{dataList.name}}</div>
      <div>开始时间：{{dataList.startTime}}</div>
      <div>状态：{{dataList.status}}</div>
    </div>
  </div>
</template>

<script>
import FormPlus from '@/components/FormPlus.vue';
export default {
  components: {
    FormPlus,
  },
  data () {
    return {
      formList: [
        { label: '编号', model: 'applyNumber', placeholder: '请输入编号' },
        { label: '名称', model: 'name', placeholder: '请输入名称' },
        { type: 'date-picker', label: '开始时间', model: 'startTime', valueFormat: 'yyyy-MM-dd HH:mm:ss', placeholder: '请选择开始时间' },
        { type: 'select', label: '状态', model: 'status', placeholder: '请选择状态', options: [{
            value: '选项1',
            label: '启用'
          }, {
            value: '选项2',
            label: '禁用'
          }] },
      ],
      dataList:{}
    };
  },
  methods: {
    // 可以取到子组件传递过来的数据
    searchPage (ruleForm) {
      this.dataList = ruleForm
      this.formList[3].options.forEach(item=>{
        if(item.value == ruleForm.status){
          this.dataList.status = item.label
        }
      })
      console.log(ruleForm, 'ruleForm');
    },
    resetForm () {
      this.dataList = {}
      console.log('重置')
    },
  },
};
</script>