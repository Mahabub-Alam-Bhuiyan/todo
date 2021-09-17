<template>
  <div class="about">
   <div class="container">
     <h3>Todos</h3>
       <div class="row">
         <div class="col-sm-6">
           <div v-for="(todo,index) in todos" :key="index" class="todo-item row" :class="{'todo-item-done' : todo.done}">
             <div class="col-sm-9">
               <div class="text">

                 <input v-if="todos[index].edit" v-model="todoedit" @keydown.enter="editupdate(index)" type="text">

                  <h3 >{{ todo.text }}</h3>

                 <small>{{ todo.timeZone.toString() }} </small>
               </div>
             </div>
             <div class="col-sm-3">
               <button @click="removeitem(index)"  style="color: #ff0000">&times;</button>
               <button v-if="!todo.done" @click="masrkasdone(index)" style="color: #026002">&check;</button>
               <button v-else @click="markasundone(index)" style="color: #d47a17">&#8630;</button>
               <button @click="Edit(index)" style="color: #d47a17">  <i class="fas fa-pencil-alt"></i> </button>
             </div>
           </div>
           <div v-if="todos.length == 0" class="no-task todo-item">
             You don't have any task to do
           </div>


         </div>

         <div class="col-sm-6">
           <div class="add-new">
            <h3>Add a todo</h3>
             <input
                 @keydown.enter="addtodo"
                 v-model="todotext" type="text">
           </div>
         </div>

     </div>
   </div>

  </div>
</template>


<script>
import { defineComponent , reactive ,ref } from 'vue'

export default defineComponent({

  setup(){
    const todos = reactive([ ]);

    const todotext = ref(" ");

    const todoedit = ref(" ");




    function addtodo(){
      todos.unshift({
        text: todotext.value,
        timeZone: Date(),
        done: false,
        edit: false,
        update: false
      });
      todotext.value = "" ;
    }

function editupdate(index){


  todos[index].text = todoedit.value

  todoedit.value = "" ;
  todos[index].edit = false

}


    function masrkasdone(index){
     todos[index].done = true
    }
    function  markasundone(index){
      todos[index].done = false
    }

    function Edit(index){
      todos[index].edit = true
      console.log(index)
    }


    function removeitem(index){
      if (confirm("Are You sure to remove this item?")){
        this.todos.splice(index,1)
      }
    }


       return{
         todos,
         todotext,
         addtodo,
         masrkasdone,
         markasundone,
         removeitem,
         Edit,
         editupdate,
         todoedit,

       }
  },

})
</script>


<style lang="scss">

button{
  border: none;
  background-color: transparent;
  padding-left: 20px;
  font-size: 17px;
}
.edit-button{
  background-color: #c1bebe;
  padding: 5px 25px !important;
}
.router-link-active{
  background-color:#7B68EE;
}

.about{
  text-align: left;
  padding-top: 50px;
}
.todo-item{
  border-radius: 5px;
  box-shadow: 2px 2px 4px whitesmoke,1px 1px 5px black ;
  margin: 15px 0;
  padding: 15px;
  text-align: left;
}
.todo-item-done{
  background-color: #a3eaa3;
}
.add-new{
  border-radius: 5px;
  box-shadow: 2px 2px 4px whitesmoke,1px 1px 5px black ;
  margin: 15px 0;
  padding: 15px;
  text-align: left;
}
.no-task{
  padding: 39px 20px !important;
}
input{
  width: 100%;
}
</style>
