<template>
  <div id="app">
    <section class="todoapp">
      <Header @addTodo="addTodo" /><!--이벤트등록해주기-->
      <Body :todos="todos" /><!--내려주기-->
      <Footer/>
    </section>
  </div>
</template>

<script>
import "./assets/css/main.css";

import Header from "./components/Header";
import Body from "./components/Body";
import Footer from "./components/Footer";

export default {
  components: {
    Header,
    Body,
    Footer
  },
  data (){
    return{
      todos : []
    };
  },
  methods : {
    addTodo (text){ /*header에서 받은 text */
      this.todos = [
        {
          id : new Date(),
          text,
          isDone : false
         },
        ...this.todos
      ];
    }
  }
};
</script>

<style>
</style>
