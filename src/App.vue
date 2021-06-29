<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <searchbar/>
    <span>Trending</span>
    <tag/>
    <questionlist/>
    <!-- <demo message="12345"/>
    <span v-bind:title="message">
    鼠标悬停几秒钟查看此处动态绑定的提示信息！{{message}}
    </span>
    <p v-if="seen">现在你看到我了</p>
    <p v-else>wertyui</p>
    <uol>
    <li v-for="todo in todos" v-bind:key="todo.id ">
      {{ todo.text }}
    </li>
    </uol>
    <p>{{ message }}</p>
    <button v-on:click="reverseMessage">反转消息</button>
    <p>{{ message }}</p>
    <input v-model="message"> -->

  </div>
  
  
</template>

<script>
import questionlist from './components/questionlist.vue'
// import HelloWorld from './components/HelloWorld.vue'
import searchbar from './components/searchbar.vue'
import tag from './components/tag.vue'

// import demo from './components/demo.vue'

export default {
  name: 'App',
  // data: ()=>({
  //   message: 'helloooooo'+new Date().toLocaleString(),
  //   seen: false,
  //   todos: [
  //     { id: 1, text: '学习 JavaScript' },
  //     { id: 2, text: '学习 Vue' },
  //     { id: 3, text: '整个牛项目' }
  //   ]
  // }),
  // methods: {
  //   reverseMessage: function () {
  //     this.message = this.message.split('').reverse().join('')
  //   }
  // },
  components: {
    // HelloWorld,
    searchbar,
    tag,
    questionlist
    // demo

  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
