<template>
  <div>
    <h1>这是App根组件</h1>
    <!-- TodoInput组件 -->
    <TodoInput @addtask="AddNew"></TodoInput>
    <!-- MyTodolist组件 -->
    <!-- 通过属性绑定将数据传递给子组件:todo -->
    <MyTodolist :todo="tasklist"></MyTodolist>
    <TodoButton v-model:active="btnIndex"></TodoButton>

  </div>
</template>

<script>
import MyTodolist from './components/todolist.vue'
import TodoInput from './components/todoInput.vue'
import TodoButton from './components/todobutton.vue'
export default {
  name: 'MyApp',
  components: {
    MyTodolist,
    TodoInput,
    TodoButton
  },
  data() {
    return {
      todolist:
        [
          { id: 1, task: '周一早晨9点开会', done: false },
          { id: 2, task: '周一晚上8点聚餐', done: false },
          { id: 3, task: '准备周三上午的演讲稿', done: true },
        ],
      nextId: 4,
      btnIndex:0
    }
  },
  methods: {
    AddNew(taskname) {
      // console.log(taskname)
      this.todolist.push({
        id: this.nextId,
        task: taskname,
        done: false
      })
      this.nextId++
    }
  },
  computed: {
    tasklist() {
      switch(this.btnIndex) {
        case 0:
          return this.todolist
        case 1:
          return this.todolist.filter(x=>x.done===true)
        case 2:
          return this.todolist.filter(x=>x.done!==true)
      }
    }
  }
}
</script>

<style lang="less" scoped>
</style>