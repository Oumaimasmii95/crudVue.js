<template>
  <div>
    <div>
      <h1>click on delete icon to delete the new person</h1>
      <div class="click on delete icon to delete the new person">
        <div
          v-for="todo in allTodos"
          class="todo"
          v-bind:key="todo.key"
        >
          {{ todo.title }}
    <i class="fas fa-trash-alt" v-on:click="deleteTodo(todo.id)"></i>

        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { mapGetters , mapActions } from 'vuex' ;
export default {
    name:"Todos" , 
    methods:{
      ...mapActions(["fetchTodos","deleteTodo","updatedTodo"]),
      onDblClick(todo) {
      const updatedTodo = {
        id: todo.id,
        title: todo.title,
        firstName:todo.firstName,
        completed: !todo.completed
      }
      this.updateTodo(updatedTodo);
    }
  },
    computed: mapGetters(["allTodos"]),
     created() {
    this.fetchTodos();
  }

}

</script>
<style scoped>
  .todos {
    display: grid;
    grid-template-columns: repeat(3, 1fr);
    grid-gap: 1rem;
  }
  .todo {
    border: 1px solid #ccc;
    background: #8bb9ee;
    padding: 1rem;
    border-radius: 5px;
    text-align: center;
    position: relative;
    cursor: pointer;
  }
  i {
    position: absolute;
    bottom: 10px;
    right: 10px;
    color: rgb(207, 19, 19);
    cursor: pointer;
  }
  .legend {
    display: flex;
    justify-content: space-around;
    margin-bottom: 1rem;
  }
  .complete-box,
  .incomplete-box {
    display: inline-block;
    width: 10px;
    height: 10px;
  }
  .complete-box {
    background: #35495e;
  }
  .incomplete-box {
    background: #60acdf;
  }
  .is-complete {
    color: #fff;
    background: #35495e;
  }
  @media (max-width: 500px) {
    .todos {
      grid-template-columns: 1fr;
    }
  }
</style>