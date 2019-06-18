<template>
  <div id="app">
    <todo-header></todo-header>
    <todo-input @passItem="addItem"></todo-input>
    <todo-list :propsItems="todoItems" :showEmpty="showEmpty" @passClear="showEmpty=true"></todo-list>
    <todo-footer :clearAvail="showEmpty" @passClear="clearItem"></todo-footer>
  </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput'
import TodoList from './components/TodoList'
import TodoFooter from './components/TodoFooter'

export default {
  name: 'app',
  components: {
    TodoHeader,
    TodoInput,
    TodoList,
    TodoFooter
  },
  data() {
    return {
      todoItems: [],
      showEmpty: true
    }
  },
  created() {
    for (let i = 0; i < localStorage.length; i++) {
      if (localStorage.getItem(localStorage.key(i)) !== 'SILENT') {
        this.todoItems.push(localStorage.getItem(localStorage.key(i)));
      }
    }
    if (this.todoItems.length) {
      this.showEmpty = false;
    }
  },
  methods: {
    addItem(item) {
      this.showEmpty = false;
      if (!localStorage.getItem(item)) {
        localStorage.setItem(item, item);
        this.todoItems.push(item);
      } else {
        alert('이미 등록된 할 일입니다.');
      }      
    },
    clearItem() {
      if (confirm('초기화하시겠습니까?')) {
        localStorage.clear();
        this.todoItems = [];
        this.showEmpty = true;
      }
    }
  }
}
</script>

<style>
  * { margin: 0; padding: 0; }
  body {
    width: 95%;
    margin: 0 auto;
    text-align: center;
    background: linear-gradient(to right, #d0e2ae, #9dc454);
  }
  .shadow {
    box-shadow: 0 5px 10px rgba(0,0,0,.05);
  }
</style>
