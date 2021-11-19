<template>
  <div id="app">
      
        <div class="row root">
            <Search />
        </div>
      </div>
 
</template>

<script>
import Search from './components/Search.vue';
export default {
  name: 'App',
  components:{
    Search,
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top:10px;
}
.root{
  margin-left:10px;
  margin-right:10px;
  display:flex;
  position: relative;
  left:40px;
  right:40px;
}
.root a{
  text-decoration: none;
}


</style>
