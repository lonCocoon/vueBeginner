<template>
  <div id="app">
    <Header/>
    <CommentBox/>
    <CommentList/>
    <Paging/>
  </div>
</template>

<script>
import Header from './components/Header'
import CommentBox from './components/CommentBox'
import CommentList from './components/CommentList'
import Paging from './components/Paging'

export default {
  name: 'App',
  components: {
    Header,
    CommentList,
    Paging
	}
}
</script>


<style>
#app {
  font-family: '微软雅黑','Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding-top:20px;
  width:900px;margin:0 auto;
}
</style>


