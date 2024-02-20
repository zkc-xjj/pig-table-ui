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
    props: {
        tableData:{
            type: Array,
            default: () => []
        }
    },
    date() {
        return {
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
  