<template>
  <section>
    <!-- 发布区域 -->
        <comment-box 
          :id="id" 
          :publisher="publisher"  
          :content="content"  
          :date="date"
          v-on:submit="addList"
        >
        </comment-box>


    <!-- 评论显示区域 -->

    <el-footer>
      <el-table :data="listPart" :show-header="true" :row-class-name="tableRowClassName"  >
        <el-table-column prop="id" label="ID" width="200"></el-table-column>
        <el-table-column prop="publisher" label="发评人" width="100"></el-table-column>
        <el-table-column prop="content" label="内容"></el-table-column>
        <el-table-column prop="date" label="日期" width="200" ></el-table-column>
      </el-table>

    <!-- <ul v-if="totalData<=pageSize">
      <li  v-for="item in listDate" >
        {{item.id}}oooooooo{{item.publisher}}oooooooo{{item.content}}oooooooo{{item.date}}
      </li>
    </ul>-->
    </el-footer> 
  </section> 
</template>


<style>
/* .el-table .rowShow {
    display: none;
} */

</style>


<script>
import CommentBox from './CommentBox'
import Paging from './Paging'

export default {
  name: 'CommentList',
  data () {
    return {
      postText:'',
      listDate:[],//所有数据
      listPart:[],//每页数据
      totalData:0, //默认数据总数
      currentPage: 1,//默认当前页码
      pageSize:5,//默认每页数据量
      toalPages:1,//最大总页数
      beginRow:1//开始行
    }
  },
  components: {
    CommentBox,
    Paging
  },
  methods:{
    tableRowClassName({row, rowIndex}) {
        if ((rowIndex+1) > this.pageSize){
            return 'rowShow'
        } 
        else {
           return '';
        }
    },
    addList(data){
    this.currentPage = 1;
    let UserId = Math.random().toString().substring(2,11);
    let commentText = this.postText.trim();
    let nowDate = new Date().toLocaleString();
    if (commentText) {
			this.listDate.unshift({
        id:UserId,
        publisher: '柚子',
        content: commentText,
        date:nowDate
      })
      let listPart = this.listDate.slice(this.beginRow-1);
      this.listPart = listPart;
      this.postText="";
      this.totalData = this.listDate.length;
    }
      
  },

    handleCurrentChange(val){
      this.currentPage = val;
      let beginRow = (this.pageSize*this.currentPage) - (this.pageSize - 1);
      let listPart  = this.listDate.slice(beginRow-1);
      this.listPart = listPart;
  }
}
}
</script>

<style scoped>
.btn{
  margin-top: 20px;
}

.block{
  text-align: center;
  padding-top: 20px;
}

</style>

