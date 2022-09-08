<!--
 * @ Author: lj
 * @ Create Time: 2022-08-29 21:05:39
 * @ Modified by:
 * @ Modified time: 2022-08-31 16:29:27
 * @ Description: 分页组件封装
 -->

<template>
  <div :class="{'hidden':hidden}" class="pagination-container">
    <el-pagination
        :background="background"
        :current-page.sync="currentPage"
        :page-size.sync="pageSize"
        :layout="layout"
        :page-sizes="pageSizes"
        :pager-count="pagerCount"
        :total="total"
        v-bind="$attrs"
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"
    />
  </div>
</template>

<script>
export default {
  name: 'pagination',
  props: {
    total: {
      required: true,
      type: Number
    },
    page: {
      type: Number,
      default: 1
    },
    limit: {
      type: Number,
      default: 20
    },
    pageSizes: {
      type: Array,
      default() {
        return [10, 20, 30, 50]
      }
    },
    // 移动端页码按钮的数量端默认值5
    pagerCount: {
      type: Number,
      default: document.body.clientWidth < 992 ? 5 : 7
    },
    layout: {
      type: String,
      default: 'total, sizes, prev, pager, next, jumper'
    },
    background: {
      type: Boolean,
      default: true
    },
    autoScroll: {
      type: Boolean,
      default: true
    },
    hidden: {
      type: Boolean,
      default: false
    }
  },
  computed: {
    // 当前页处于第几页
    currentPage: {
      get() {
        return this.page
      },
      set(val) {
        this.$emit('update:page', val)
      }
    },
    // 当前页条数
    pageSize: {
      get() {
        return this.limit
      },
      set(val) {
        this.$emit('update:limit', val)
      }
    }
  },
  methods: {
    // el-pagination 组件自定义事件回调 参数val：当前页码一共多少条数据
    handleSizeChange(val) {
      // 触发父组件pagination自定义事件 传递当前页码数currentPage跟当前页显示多少条数limit
      this.$emit('pagination', { page: this.currentPage, limit: val })
      if (this.autoScroll) {
        console.log('1111111111',this.autoScroll)
      }
    },
    // el-pagination 组件自定义事件回调 参数val：当前页码处于第几页
    handleCurrentChange(val) {
      // 触发父组件pagination自定义事件 传递当前页码数currentPage跟当前页显示多少条数limit
      this.$emit('pagination', { page: val, limit: this.pageSize })
      if (this.autoScroll) {
        console.log('2222222222',this.autoScroll)
      }
    }
  }
}
</script>

<style scoped>
.pagination-container {
  background: #fff;
  padding: 32px 16px;
}
.pagination-container.hidden {
  display: none;
}
</style>