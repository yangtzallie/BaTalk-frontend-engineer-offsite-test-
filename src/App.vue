<template>
  <div id="app">
    
    <searchbar/>
    <div class="trending"><span>Trending</span></div>
    <tag/>
    <div class="questionlist"><questionlist/></div>
  </div>
  
  
</template>

<script>
import questionlist from './components/questionlist.vue'
import searchbar from './components/searchbar.vue'
import tag from './components/tag.vue'

export default {
  name: 'App',

  components: {
    searchbar,
    tag,
    questionlist
  }
}
</script>

<style scoped>


/*#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}*/

#app {
  display: flex;
  background-color:white;
  flex-direction: column;
  max-width: 1000px;
  height: 100vh;
  margin: auto;
}
.questionlist{
  flex-grow: 1;
  min-height: 0;
}
.trending{
  font-size: 24px;
}


</style>
