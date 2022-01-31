
<template>
  <div>
    <h3>add the person : fist Name , Last name : email adress </h3>
    <div class="add">
      <form @submit="onSubmit">
        <input type="text" v-model="title" placeholder="first name" required />
        <input type="text" v-model="secondName" placeholder="Second Name" required />
        <input type="text" v-model="emailAddress" placeholder="email Adress" required />
        <input type="submit" value="Submit">
      </form>
    </div>
  </div>
</template>

<script>
import { mapActions } from 'vuex';

export default {
  name: "AddTodo",
  data() {
    return {
      title: '',
      secondName: '',
      
    }
     
  
  },
  methods: {
    ...mapActions(["addTodo"]),
    onSubmit(event) {
      event.preventDefault();
      this.addTodo(this.title);

      this.title = '';
      this.firstName(this.firstName);
      this.firstName = '';
    }
    
      
    }
  }

</script>

<style scoped>
  form {
    display: flex;
  }

  input[type="text"] {
    flex: 10;
    padding: 10px;
    border: 1px solid #4171b8;
    outline: 0;
  }

  input[type="submit"] {
    flex: 2;
    background: #41a6b8;
    color: #fff;
    border: 1px solid #41b883;
    cursor: pointer;
  }
</style>
