<template>
      <el-main>
      <el-input
        type="textarea" 
        :autosize="{ minRows: 2, maxRows:6}" 
        placeholder="我是输入框，来评论吧" 
        v-model="postText"  
        >
      </el-input>

      <el-button 
      class="btn" 
      type="primary" 
      icon="el-icon-edit" 
      plain 
      v-on:click="addList">发布</el-button>
    </el-main>
</template>

<style>
/* .el-table .rowShow {
    display: none;
} */

</style>


<script>

export default {
  name: 'CommentBox',
  props:{
    postText:String
  },
  data: function () {
    return {
      postText:''
    }
  },
  methods: {
    addList: function() {
      this.$emit("submit",this.postText);
      this.postText="";
      console.log("评论")


  },
  computed: {//计算属性

  }
}
}

</script>

<style scoped>
.btn{
  margin-top: 20px;
}

</style>

