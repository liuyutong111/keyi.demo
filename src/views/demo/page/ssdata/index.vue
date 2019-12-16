<template>
  <d2-container>
    <template slot="header">{{$t('page1')}}</template>
    <div class="sstop">
      <el-input
        placeholder="搜索关键字"
        v-model="input"
        clearable class="ss_search">
      </el-input>
      <el-button type="success">查询</el-button>
    </div>

    <el-table
      :data="tableData"
      stripe
      style="width: 100%">
      <el-table-column
      type="selection"
      align="center"
      >
      </el-table-column>
      <el-table-column
        prop="sb_name"
        align="center"
        label="设备名称">
      </el-table-column>
      <el-table-column
        prop="sbid"
        align="center"
        label="设备编码">
      </el-table-column>
      <el-table-column
        prop="current_num"
        align="center"
        label="当前值">
      </el-table-column>
      <el-table-column
        prop="process_stu"
        align="center"
        label="处理状态">
      </el-table-column>
      <el-table-column
        prop="Solar_voltage"
        align="center"
        label="太阳能电压">
      </el-table-column>
      <el-table-column
        prop="battery_power"
        align="center"
        label="电池电量">
      </el-table-column>
      <el-table-column
        prop="installation_site"
        align="center"
        label="安装位置">
      </el-table-column>
      <el-table-column
        prop="upload_time"
        align="center"
        label="上传时间">
      </el-table-column>
      <el-table-column
        prop="operate"
        align="center"
        label="操作">
        <template slot-scope="scope">
          <el-button @click="handleClick(scope.row)" type="text" size="small">查看</el-button>
          <el-button type="text" size="small" @click="open">删除</el-button>
        </template>
      </el-table-column>
    </el-table>
    <div class="block">
      <el-pagination
        @size-change="handleSizeChange"
        @current-change="handleCurrentChange"

        :page-size="100"
        layout=" prev,  pager, next,sizes, jumper"
        :page-sizes="[100, 200, 300, 400]"
        background
        :total="400">
      </el-pagination>
    </div>

  </d2-container>
</template>

<script>
export default {
  name: 'ssdata',
  data () {
    return {
      input: '',
      tableData: [{
        sb_name: 'name',
        sbid: 'id',
        current_num: '000',
        process_stu: '处理中',
        Solar_voltage: '未知',
        battery_power: '100%',
        installation_site: '暂时未知',
        upload_time: '2019.12.16'
      }, {
        sb_name: 'name',
        sbid: 'id',
        current_num: '000',
        process_stu: '处理中',
        Solar_voltage: '未知',
        battery_power: '100%',
        installation_site: '暂时未知',
        upload_time: '2019.12.16'
      }, {
        sb_name: 'name',
        sbid: 'id',
        current_num: '000',
        process_stu: '处理中',
        Solar_voltage: '未知',
        battery_power: '100%',
        installation_site: '暂时未知',
        upload_time: '2019.12.16'
      }]
    }
  },
  methods: {
    handleClick (row) {
      console.log(row)
    },
    // 删除
    open () {
      this.$confirm('此操作将永久删除该文件, 是否继续?', '提示', {
        confirmButtonText: '确定',
        cancelButtonText: '取消',
        type: 'warning',
        center: true
      }).then(() => {
        this.$message({
          type: 'success',
          message: '删除成功!'
        })
      }).catch(() => {
        this.$message({
          type: 'info',
          message: '已取消删除'
        })
      })
    },
    handleSizeChange (val) {
      console.log(`每页 ${val} 条`)
    },
    handleCurrentChange (val) {
      console.log(`当前页: ${val}`)
    }
  }
}
</script>

<style lang="scss" scoped>
  .sstop{
    width: 25%;
    margin-bottom: 1.2rem;
  }
  .ss_search{
    width: 50%;
    margin-right: 0.5rem;
  }
</style>
