<template>
  <div>
    <ul>
<<<<<<< Updated upstream
      <li v-for="(todoItem, index) in todoItems" v-bind:key="todoItem" class="shadow">
        <i class="checkBtn fas fa-check" v-on:click="toggleCompleted"></i>
        {{ todoItem }}
=======
      <li v-for="(todoItem, index) in propsdata" v-bind:key="todoItem.item" class="shadow">
        <i class="checkBtn fas fa-check" v-bind:class="{checkBtnCompleted: todoItem.completed}" 
          v-on:click="toggleCompleted(todoItem, index)"></i>
        <span v-bind:class="{textCompleted: todoItem.completed}">{{ todoItem.item }}</span>
>>>>>>> Stashed changes
        <span class="removeBtn" v-on:click="removeTodo(todoItem, index)"> 
          <i class="fa fa-trash" aria-hidden="true"></i>
        </span>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: ['propsdata'],
  methods: {
    removeTodo: function(todoItem, index){
      console.log(this.todoItems, index);
      localStorage.removeItem(todoItem)
      this.todoItems.splice(index, 1)
    },
    toggleCompleted: function() {
      console.log('toggle')
    }
  },
<<<<<<< Updated upstream
  created: function() {
    if (localStorage.length > 0) {
      for (let i=0; i < localStorage.length; i++) {
        if (localStorage.key(i) !== 'loglevel:webpack-dev-server'){
          this.todoItems.push(localStorage.key(i));
        }
      }
    }
  }
=======

>>>>>>> Stashed changes
}
</script>

<style scoped>
ul {
  list-style-type: none;
  padding-left: 0px;
  margin-top:0px;
  text-align: left;
}
li {
  display: flex;
  height:50px;
  line-height: 50px;
  margin: 0.5rem;
  padding: 0 0.9rem;
  background: white;
  border-radius: 5px;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}
.checkBtn {
  line-height:50px;
  padding:0 10px 0 0;
  color: #64bde6;
}
</style>