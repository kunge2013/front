<template>
    <pagination
      :total="total"
      :page.sync="listQuery.page"
      :limit.sync="listQuery.limit"
      @pagination="getList" />
  </template>
  
  <script>
  import Pagination from '@/components/Pagination'
  
  export default {
    components: { Pagination },
    data() {
      return {
        total: 0,
        listQuery: {
          page: 1,
          limit: 20
        }
      }
    },
    methods: {
      getList() {
        // 获取数据
      }
    }
  }
  </script>