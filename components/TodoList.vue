<template>

  <div class="todo-list">
    <div class="card">
      <div class="card-header">
        Количество дел: {{ todoList.length }}
      </div>

      <div class="card-body">
        
        <form class="form-group mb-3" @submit.prevent>
          <div class="input-group">
            <input type="text" class="form-control" v-model="todo" @keyup.enter="handleChangeInput">
            
            <div class="input-group-append">
              <button class="btn btn-outline-secondary" :disabled="todo.length !== 0" @click="handleAddTodo" type="button">Добавить</button>
            </div>
          </div>
        </form>

        <div class="btn-group btn-group-sm d-flex mb-3" role="group">
          <button type="button" class="btn btn-outline-secondary">All</button>
          <button type="button" class="btn btn-outline-secondary">Done</button>
          <button type="button" class="btn btn-outline-secondary">Todo</button>
        </div>

        <ul class="todo__list list-group">
          <li 
            v-for="todo in todoList" 
            :key="todo.id" 
            class="todo__item list-group-item list-group-item-action"
          >
          <div class="d-flex align-items-center justify-content-between">
            <span @click.prevent="handleClickTodo">{{ todo.title }}</span>

              <div>
                <button @click="handleDoneTodo" type="button" class="btn btn-outline-success">
                  <i class="bi bi-check-lg"></i>
                </button>
                 <button @click="handleDoneTodo" type="button" class="btn btn-outline-secondary">
                  <i class="bi bi-exclamation-lg"></i>
                </button>
                <button @click="handleDeleteTodo" type="button" class="btn btn-outline-danger">
                  <i class="bi bi-trash"></i>
                </button>
              </div>

            </div>
          </li>
        </ul> 

      </div>
    </div>
  </div>
</template>

<script>
export default {

  data: () => ({

    todo: "",
    todoItemClasses: "",
    todoList: [
      {id: 1, title: 'Learn Rect.js', complited: true},
      {id: 2, title: 'Learn Next.js', complited: false},
      {id: 3, title: 'Learn Vue.js', complited: false},
      {id: 4, title: 'Learn Nuxt.js', complited: true},
      {id: 5, title: 'Learn Other.js', complited: true},
    ]
  }),

  methods: {

    handleAddTodo() {
      this.todoList.push({
        id: this.todoList.length,
        title: this.todo,
        complited: false
      });

      this.todo = ""
    },

    handleChangeInput(event) {
      this.handleAddTodo()
    },

    handleDoneTodo(event) {
      console.log("Done", event)
 
    },

    handleDeleteTodo(event) {
     console.log(event.target.getAttribute('data-index'))
     this.todoList.splice(0,1)
    },

    handleClickTodo(event) {
      const TodoSelected = this.todoList.find(todo => todo.title === event.target.innerText);
      console.log(TodoSelected.title);
    }
  }

}
</script>

<style>
  .todo-list {
    max-width: 600px;
    margin: 0 auto;
  }

  .todo__item.active {
    color: brown;
  }
</style>