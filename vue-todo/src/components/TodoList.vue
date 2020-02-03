<template>
  <div>
    <transition-group name="list" tage="ul">
      <li v-for="(todoItem, index) in this.storedTodoItems" v-bind:key="todoItem.item" class="shadow">
        <i class="checkBtn fas fa-check" v-bind:class="{checkBtnCompleted: todoItem.completed}" 
          v-on:click="toggleCompleted({ todoItem, index })"></i>
        <span v-bind:class="{textCompleted: todoItem.completed}">{{ todoItem.item }}</span>
        <span class="removeBtn" v-on:click="removeTodo({todoItem, index})"> 
          <i class="fa fa-trash" aria-hidden="true"></i>
        </span>
      </li>
    </transition-group>
  </div>
</template>

<script>
import { mapGetters, mapMutations } from 'vuex'

export default {
  methods: {
    // removeTodo를 눌렀을 때 removeOneItem 뮤테이션이 호출 된다.
    // map 헬퍼 함수는 자동으로 인자를 넘겨준다. removeOneItem({todoItem, index})와 같음
    ...mapMutations({
      removeTodo: "removeOneItem",
      toggleCompleted: "toggleOneItem",
    }),
    // toggleCompleted(todoItem, index) {
    //   // this.$emit('toggleItem', todoItem, index)
    //   this.$store.commit('toggleOneItem', { todoItem, index })
    // }
  }, 
  computed: {
    // todoItems() {
    //   return this.$store.getters.storedTodoItems;
    // }
    ...mapGetters(['storedTodoItems'])
  },
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
.checkBtnCompleted {
  color: #b3adad;
}
.textCompleted {
  text-decoration: line-through;
  color: #b3adad;
}

/* 리스트 아이템 트렌지션 효과 */
.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to {
  opacity: 0;
  transform: translateY(30px);
}
</style>