<template>
 <div class="block"  v-if="totalData>pageSize">
        <el-pagination
          layout="prev, pager, next" 
          @current-change="handleCurrentChange"
          :current-page="currentPage"
          :page-size="pageSize"
          :total="totalData"
          :page-count="toalPages">
        </el-pagination>
    </div>

</template>

<script>

export default {
  name: 'Paging',
  data () {
        return {
          score:'',
        }
  }
	}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.block{
  text-align: center;
}

.demonstration{
    display: block;
    padding: 40px;
}


</style>

