<template>
  <div id="app">
    <section class="todoapp">
      <Header @addTodo="addTodo" /><!--이벤트등록해주기-->
      <Body :todos="todos" @updateDone="updateDone"/> <!--todo 내려주기-->
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
    },
    updateDone (id){ //데이터 접근을 하여 바꾸기 위해 : 기존이랑 똑같이 복사해 와서 거기다 작업 원본 보호
      const currentTodos = [...this.todos]; //복사함
      const todo = currentTodos.find((todo) => todo.id === id) ;
      if(todo){
        todo.isDone = !todo.isDone; 
        this.todos = currentTodos; //원본에 덮음
      }
    }
  }
};
</script>

<style>
</style>
