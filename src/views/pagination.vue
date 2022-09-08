<!--
 * @ Author: lj
 * @ Create Time: 2022-08-29 21:05:39
 * @ Modified by:
 * @ Modified time: 2022-08-31 16:29:27
 * @ Description: 分页组件使用
 -->

<template>
  <pagination
      v-show="total>0"
      :total="total"
      :page.sync="queryParams.pageNum"
      :limit.sync="queryParams.pageSize"
      @pagination="handlePagination"
  />
</template>

<script>
import Pagination from '@/components/Pagination.vue'

export default{
  components: {
    Pagination
  },
  data() {
    return {
      // 总条数
      total: 20,
      queryParams: {
        pageNum: 1,
        pageSize: 10
      }
    }
  },
  methods: {
    /* 分页回调 */
    handlePagination(val){
      console.log(val); // {page:1, limte: 10}

      // 获取列表逻辑~

      // const data = {
      //   "pageNum": val.page,
      //   "pageSize": val.limit,
      //   "wm": this.wm
      // }
      // this.tableData = []
      // this.getTb(this.tb, data)
    }
  }
}
</script>