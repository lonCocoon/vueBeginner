<template>
  <section>
    <!-- 头部 -->
    <el-header>
      <h1 v-text="title"></h1>
    </el-header>

    <!-- 发布区域 -->
    <el-main>
      <el-input
        type="textarea" :autosize="{ minRows: 2, maxRows:6}" placeholder="我是输入框，来评论吧" v-model="postText">
      </el-input>
      <el-button class="btn" type="primary" icon="el-icon-edit" plain @click="addList">发布</el-button>
    </el-main>

    <!-- 评论显示区域 -->
    <el-footer>
      <el-table :data="listPart" :show-header="false" :row-class-name="tableRowClassName">
        <el-table-column prop="id" label="ID" width="200"></el-table-column>
        <el-table-column prop="publisher" label="发评人" width="100"></el-table-column>
        <el-table-column prop="content" label="内容"></el-table-column>
        <el-table-column prop="created_at" label="日期" width="200" ></el-table-column>
      </el-table>

    <!--  分页 -->
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

    </el-footer>
  </section> 
</template>


<style>
.el-table .rowShow {
    display: none;/* 动态调用，隐藏超出每页显示数的数据 */
}
</style>


<script>
export default {
  name: 'CommentList',
  data () {
    return {
      title: '评论',
      postText:'',//输入评论内容
      listDate:[],//所有数据
      listPart:[],//每页数据
      totalData:0, //默认数据总数
      currentPage: 1,//默认当前页码
      pageSize:5,//默认每页数据量
      toalPages:1,//最大总页数
      beginRow:1//开始行
    }
  },
  methods:{
    //隐藏溢出行的显示
    tableRowClassName({row, rowIndex}) {
        if ((rowIndex+1) > this.pageSize){
            return 'rowShow'
        } 
        else {
           return '';
        }
    },
    //发布评论
    addList(){
    this.currentPage = 1;//重置 当前页数值,回到首页
    let UserId = Math.random().toString().substring(2,11);
    let commentText = this.postText.trim();
    let nowDate = new Date().toLocaleString();
    if (commentText) {
			this.listDate.unshift({
        id:UserId,
        publisher: '柚子',
        content: commentText,
        created_at:nowDate
      });

      this.postText="";
      this.totalData = this.listDate.length;
      let listPart = this.listDate.slice(this.beginRow-1);
      this.listPart = listPart;
      
    }
  },
  //改变当前页时触发
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
h1 {
  font-weight: normal;
}

.btn{
  margin-top: 20px;
}

.block{
  text-align: center;
  padding-top: 20px;
}

</style>

