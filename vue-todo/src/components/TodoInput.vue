<template>
  <div class="inputBox shadow">
    <input type="text" v-model="toDoItem" v-on:keyup.enter="addItem">
    <span class="addContainer" v-on:click="addItem">
      <i class="fas fa-plus addBtn"></i>
    </span>

    <Modal v-if="showModal" @close="showModal = false">
    <!--
      you can use custom content here to overwrite
      default content
    -->
      <h3 slot="header">
        경고!
        <i class="closeModalBtn fas fa-times" @click="showModal = false"></i>
      </h3>
      <h3 slot="body">
        무언가를 입력하세요!
      </h3>
     
    </Modal>
  </div>
</template>

<script>
import Modal from './common/Modal.vue';

export default {
  data() {
    return {
      toDoItem: '',
      showModal: false,
    }
  },
  methods: {
    addItem() {
      if (this.toDoItem !== ''){
        // this.$emit('addTodoItem', this.toDoItem)
        this.$store.commit("addOneItem", this.toDoItem);
        this.cleanInput();
      } else {
        this.showModal = !this.showModal;
      }
    },
    cleanInput() {
      this.toDoItem = '';
    }
  },
  components: {
    Modal,
  },
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
  .closeModalBtn {
    color: #42b983;
  }
</style>