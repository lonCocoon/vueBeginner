<template>
    <!-- 头部 -->
    <el-header>
      <h1 v-text="title"></h1>
    </el-header>
</template>


<script>
export default {
  name: 'Header',
  data () {
    return {
      title: '评论',
    }
  }
  
}
</script>


<style scoped>
h1 {
  font-weight: normal;
  color: red;
}
</style>
