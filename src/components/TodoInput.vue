<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="fas fa-plus addBtn"></i>
        </span>
        <!-- <button @click="addTodo">add</button> -->
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodoItem: ""
        }
    },
    methods:{
      addTodo() {
        if (this.newTodoItem !== "") {
          this.$emit("addEvent", this.newTodoItem);
          this.clearInput();
        }
      },
      clearInput() {
      //addTodo() 함수에 있었지만 clearInput()함수로 이동
      this.newTodoItem = "";
    }
    }
}
</script>

<style scoped>
input:focus {
  outline: none;
}
.inputBox {
  background: white;
  height: 50px;
  line-height: 50px;
  border-radius: 5px;
}
.inputBox input {
  border-style: none;
  font-size: 0.9rem;
}
.addContainer {
  float: right;
  background: linear-gradient(to right, #6478FB, #8763FB);
  display: block;
  width: 3rem;
  border-radius: 0 5px 5px 0;
}
.addBtn {
  color: white;
  vertical-align: middle;
}
</style>
