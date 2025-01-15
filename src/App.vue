<template>
    <div class="todo">
        <div class="todo_whole">
            <TodoHeader/>
            <TodoInput
            v-on:addTodo="addTodo"
            />
            <TodoList
            v-bind:propsdata="todoItems"
            v-on:removeTodo="removeTodo"
            />
            <TodoFooter
            v-on:removeAll="clearAll"
            />
        </div>
    </div>
</template>

<script>
import TodoHeader from './components/TodoHeader.vue'
import TodoInput from './components/TodoInput.vue'
import TodoList from './components/TodoList.vue'
import TodoFooter from './components/TodoFooter.vue'

export default {
    components:{
        TodoHeader,
        TodoList,
        TodoInput,
        TodoFooter
    },

    data() {
        return {
            todoItems: []
        };
    },
    
    methods: {
        clearAll() {
            localStorage.clear();
            this.todoItems = [];
        },
        addTodo(todoItem) {
            localStorage.setItem(todoItem, todoItem);
            this.todoItems.push(todoItem);
        },
        removeTodo(todoItem, index) {
            localStorage.removeItem(todoItem);
            this.todoItems.splice(index, 1);
        }
    },

    created() {
        if (localStorage.length > 0) {
            for (var i = 0; i < localStorage.length; i++) {
                this.todoItems.push(localStorage.key(i));
            }
        }
    },
}
</script>

<style>
  @import url('./assets/scss/_common.scss');
  @import url('./assets/scss/_reset.scss');
  @import url('https://pro.fontawesome.com/releases/v5.10.0/css/all.css');
  @import url('https://fonts.googleapis.com/css2?family=Itim&display=swap');
</style>
