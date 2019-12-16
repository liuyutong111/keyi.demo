<template>
  <d2-container>
    <template slot="header">{{$t('page1')}}</template>
      <div class="sjtop">
        <el-select v-model="value" placeholder="请选择设备名称">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-select v-model="value" placeholder="请选择设备线路">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-select v-model="value" placeholder="请选择所在区域">
          <el-option
            v-for="item in options"
            :key="item.value"
            :label="item.label"
            :value="item.value">
          </el-option>
        </el-select>
        <el-date-picker
          v-model="value1"
          type="date"
          placeholder="选择日期">
        </el-date-picker>
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
        prop="sb_circuit"
        align="center"
        label="设备线路">
      </el-table-column>
      <el-table-column
        prop="sb_area"
        align="center"
        label="所属区域">
      </el-table-column>
      <el-table-column
        prop="current_num"
        align="center"
        label="当前值">
      </el-table-column>
      <el-table-column
        prop="update_time"
        align="center"
        label="状态更新时间">
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
  name: 'sjanalysis',
  data () {
    return {
      options: [{
        value: '选项1',
        label: '黄金糕'
      }, {
        value: '选项2',
        label: '双皮奶'
      }, {
        value: '选项3',
        label: '蚵仔煎'
      }, {
        value: '选项4',
        label: '龙须面'
      }, {
        value: '选项5',
        label: '北京烤鸭'
      }],
      value: '',
      value1: '',
      tableData: [{
        sb_name: 'name',
        sb_circuit: '线路',
        sb_area: '北京',
        current_num: '000',
        update_time: '2019.12.16'
      },
      {
        sb_name: 'name',
        sb_circuit: '线路',
        sb_area: '北京',
        current_num: '000',
        update_time: '2019.12.16'
      },
      {
        sb_name: 'name',
        sb_circuit: '线路',
        sb_area: '北京',
        current_num: '000',
        update_time: '2019.12.16'
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
  .sjtop{
    width: 100%;
    display: flex;
    justify-content: space-between;
    margin-bottom: 1.2rem;
  }
</style>
