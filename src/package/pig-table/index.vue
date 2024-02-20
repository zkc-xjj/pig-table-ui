<template>
    <div class="hello">
        <el-table :data="tableData" :row-key="getRowKeys" @selection-change="handleSelectionChange">
            <el-table-column type="selection" width="55">
            </el-table-column>
            <el-table-column label="日期" width="120">
                <template slot-scope="scope">{{ scope.row.date }}</template>
            </el-table-column>
            <el-table-column prop="name" label="姓名" width="120">
            </el-table-column>
            <el-table-column prop="address" label="地址" show-overflow-tooltip>
            </el-table-column>
        </el-table>
    </div>
</template>
  
<script>
export default {
    name: 'HelloWorld',
    date() {
        return {
            tableData: [
                {
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
                }
            ],
            multipleSelection: []
        }
    },
    methods: {
        getRowKeys(row) {
            return row.id;
        },
        // 选中值
        handleSelectionChange(val) {
            const extractedIDs = [];
            val.forEach(item => {
                if (item && item.id) {
                    extractedIDs.push(item.id);
                }
            });
            this.multipleSelection = extractedIDs;
            this.$emit('transfer', this.multipleSelection)
        }
    }
}
</script>
  
<style scoped></style>
  