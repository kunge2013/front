<template>
  <div>
    <el-table
      :data="tableData"
      style="width: 100%">
      <el-table-column
        prop="date"
        label="日期"
        width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="address"
        label="地址">
      </el-table-column>
    </el-table>

    <pagination
      :total="pageInfo.total"
      :page.sync="pageInfo.listQuery.page"
      :limit.sync="pageInfo.listQuery.limit"
      @pagination="getList" />
  </div>
</template>
  
  <script>
  import Pagination from '@/components/Pagination'
  
  export default {
    components: { Pagination },
    data() {
      return {
        tableData: [{
            date: '2016-05-02',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1518 弄'
          }, {
            date: '2016-05-04',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1517 弄'
          }, {
            date: '2016-05-01',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1519 弄'
          }, {
            date: '2016-05-03',
            name: '王小虎',
            address: '上海市普陀区金沙江路 1516 弄'
          }],
        pageInfo:{
        total: 0,
        listQuery: {
          page: 1,
          limit: 20
        }
      }
    }
    },
    methods: {
      getList() {
        // 获取数据
        console.info(this.data)
      }
    }
  }
  </script>