<template>
  <div id="app">
    <CommentList/>
  </div>
</template>

<script>
import CommentList from './components/CommentList'

export default {
  name: 'App',
  components: {
		CommentList
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


