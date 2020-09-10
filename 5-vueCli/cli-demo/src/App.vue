<template>
  <div id="app">
    {{message}}
    <div v-bind:id="message"></div>
    <todo-list>
        <todo-item @delete="handleDelete" v-for="item in list" :key="item.title" :title="item.title" :del="item.del" data-test="dd">
            <template  v-slot:pre-slot="{value}"> 
                <span>前置图标{{value}}</span>   
            </template>

            <template v-slot:suf-slot>
                <span >后置图标</span>   
            </template>
        </todo-item>
    </todo-list>
  </div>
   
</template>

<script>
import TodoItem from "./components/TodoItem.vue"
import TodoList from './components/TodoList.vue'

export default {
  name: 'App',
  components: {
    TodoItem,
    TodoList
  },
  data(){
    return {
      message: 'hello world',
      item: {
          title: '课程1',
          del: false
      },
      list: [{
                  title: '课程1',
                  del: false
              },
              {
                  title: '课程2',
                  del: true
              }
      ],
    }
  },
  methods:{
      handleDelete(val){
          console.log('handleDelte',val);
      }
  }
  
}
</script>

<style>
</style>
