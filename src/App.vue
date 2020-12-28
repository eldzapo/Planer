<template>
  <div id="app">
    <h1></h1>
    <b-container>
        <b-row id="b-row"> 
            <b-col class="col-lg-6" >
             <Forma />
            </b-col>
             <b-col class="col-lg-6" >
               <Todo/>
          </b-col>
        </b-row>
     </b-container> 
  </div>
</template>

<script>


import Todo from './components/Todo.vue'
import Forma from './components/Forma.vue'

export default {
  name: 'App',
  components: {
    Todo,
    Forma
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
  min-height:800px;
  background-color:#ECECEF;
  margin-top:-10px;
}

</style>
