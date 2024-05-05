<template>
  <body>
    <div class="container">
        <h1 class="heading">TO-DO APP</h1>

        <div class="user-role">
            <select v-model="role" class="select">
                <option value="admin">Admin</option>
                <option value="user">User</option>
            </select>
        </div>

        <div class="display" v-if="role === 'admin'">
            <form action="" @submit.prevent="calculate">
              <input v-model="todo" type="text" class="input" :disabled="role === 'user'">
              <button @click="add" class="btn-eqal" type="submit">Add</button>
            </form>
        </div>
        <div class="operator" v-if="role === 'admin'">
          <button @click="all" class="btn-operator">Delete All</button>
        </div>

        <h1>Your Task</h1>
        <section v-for="(task, id) in tasks" :key="task.id">
            <div class="section ">
              <button @click="Read"><svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512"><path d="M464 256A208 208 0 1 0 48 256a208 208 0 1 0 416 0zM0 256a256 256 0 1 1 512 0A256 256 0 1 1 0 256z"/></svg></button>
                <p>{{ task.title }}</p> 
                <button @click="remove(id)" class="button-delete" v-if="role === 'admin'">X</button>  
            </div>
        </section>
    </div>
  </body>
  
</template>

<script>
  export default {
    data(){
      return{
        todo: "",
        tasks: [
        {
    "userId": 1,
    "id": 1,
    "title": "delectus aut autem",
    "completed": false
  },
  {
    "userId": 1,
    "id": 2,
    "title": "quis ut nam facilis et officia qui",
    "completed": false
  },
  {
    "userId": 1,
    "id": 3,
    "title": "fugiat veniam minus",
    "completed": false
  },
  {
    "userId": 1,
    "id": 4,
    "title": "et porro tempora",
    "completed": true
  },
        ],
        role: 'user',
      };
    },
    methods:{
      add(){
        if(this.todo){
          this.tasks.push({
            title:this.todo,
            completed: false,
          });
          this.todo = '';
        }
      },
      remove(id){
        this.tasks.splice(id,1)
      },
      all(){
        this.tasks = [];
      },
    },
  }
</script>

<style>
    body{
      margin-top: 40px;
    }
    .container{
      padding: 50px;
      border-radius: 20px;
      min-height: 10vh;
      min-width: 45vh;
      background-color: rgb(91, 145, 186);
      box-shadow: 2px 2px 4px #b7b7b7;
      margin: auto;
      width: 30%;
    }
    h1{
      margin-top: 0px;
      align-items: center;
      text-align: center;
    }
    button{
      border: none;
      background-color: transparent;
      color: rgb(253, 253, 253);
      padding: 5px;
      margin: 10px;
      cursor: pointer;
    }
    .display{
      display: flex;
      align-items: center;
      justify-content: center;
      box-shadow: 1px 1px 3px 3px #4d4d4d;
      border-radius: 20px;
    }
    .input{
        color: rgb(250, 250, 250);
        background-color: transparent;
        padding: 10px 80px 15px 20px;
        border: none;
        outline: none;
        border-bottom: 2px solid rgb(22, 23, 21);                
     }
     .operator{
      margin: auto;
      width: 50%;
     }
     .btn-operator{
        margin: 25px 0px;
        border: none;
        background-color: rgb(69, 198, 142);
        border-radius: 20px;
        padding: 12px 60px;
        box-shadow: 2px 2px 4px #000000;
     }
     .btn-eqal{
        background-color: rgb(200, 227, 102);
        border-radius: 20px;
        padding: 20px 23px;
        box-shadow: 2px 2px 4px #000000;
     }
     .button-delete{
        background-color: rgba(255, 62, 62, 0.589);
        box-shadow: 2px 2px 4px #000000;
        border-radius: 50%;
        padding: 10px 12px;
    } 
    .section{
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-top: 20px;
        padding: 10px 20px;
        box-shadow: 2px 2px 4px #000000;
        border-radius: 20px;
        background: rgb(1, 121, 151);
        border: 1px solid #555;
        color: azure;
    }
    .completed{
      text-decoration: line-through;
    }
    section svg{
      height: 1rem;
    }
    .user-role{
        margin-bottom: 20px;
        text-align: center;
    }
    .select{
        padding: 5px 20px;
        border-radius: 20px;
        border: 1px solid #555;
        background-color: rgb(69, 198, 142);
        color: white;
        font-weight: bold;
        cursor: pointer;
    }
</style>
