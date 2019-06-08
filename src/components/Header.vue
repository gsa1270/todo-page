<template>
  <header class="header">
    <h1>todos</h1>
    <input
      v-model="text"
      class="new-todo"
      autofocus
      autocomplete="off"
      placeholder="What needs to be done?"
      @keypress="handleInput" 
    >
    <!--keyup , keypress -->
  </header>
</template>

<script>
export default {
  data() {
    return {
      text: ""
    };
  },
  methods: {
    handleInput(event) {
     // console.log(event.keyCode); /*각각의 고유값 enter : 13번 */
      if(event.keyCode == 13){
        if(!this.text) return; //공백값 처리하기
        this.$emit('addTodo' , this.text); //$emit  data 넣어주기
        this.text ='';
        
      }
      
    }
  }
};
</script>

<style>
h1 {
  position: absolute;
  top: -155px;
  width: 100%;
  font-size: 100px;
  font-weight: 100;
  text-align: center;
  color: rgba(175, 47, 47, 0.15);
  -webkit-text-rendering: optimizeLegibility;
  -moz-text-rendering: optimizeLegibility;
  text-rendering: optimizeLegibility;
}
</style>