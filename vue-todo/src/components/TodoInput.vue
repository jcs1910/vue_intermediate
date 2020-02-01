<template>
  <div class="inputBox shadow">
    <input type="text" v-model="toDoItem" v-on:keyup.enter="addItem">
    <span class="addContainer" v-on:click="addItem">
      <i class="fas fa-plus addBtn"></i>
    </span>
  </div>
</template>

<script>
export default {
  data: function() {
    return {
      toDoItem: ''
    }
  },
  methods: {
    addItem: function() {
      // 아이템이 있을 때
      if (this.toDoItem !== '') {
        const obj = {completed: false, item: this.toDoItem};
        localStorage.setItem(this.toDoItem, JSON.stringify(obj));
        this.cleanInput();
      }
    },
    cleanInput: function() {
      this.toDoItem = '';
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
    height:50px;
    line-height: 50px;
    border-radius: 5px;
  }
  .inputBox input {
    border-style:none;
    font-size: 0.9rem;
  }
  .addContainer {
    float: right;
    background: linear-gradient(to right, #6478FB, #8763FB);
    display:block;
    width: 3rem;
    border-radius: 0 5px 5px 0;
  }
  .addBten {
    color: white;
    vertical-align: middle;
  }
</style>