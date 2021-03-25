<template>
    <section class="todoapp">
        <header class="header">
            <h1>Voici ma liste de taches <span class="btn btn-outline-primary">Todo</span></h1>
            <br>
            <label for="text">Ajouter une tache</label> <!-- <input type="text" class="todo">  -->
            
            <div class="input-group mb-3">
                <button class="btn btn-outline-secondary" type="button" @click="addTodo">Add</button>
                <input type="text" class="form-control" placeholder="Ajouter une tâche" v-model="newTodo" @keyup.enter=addTodo required>
            </div>
        </header>
        
        <!-- <ul class="list-group" v-for="todo in todos" :key="todo.name"> <li class="list-group-item" v-on:remove="todos.splice(index, 0)"> {{todo.name}}</li>  <div> --> <!-- <label class="list-group-item">{{todo.name}}</label> --> <!-- <li class="list-group-item"> {{todo.name}}</li> --> <!-- </div> --> <!-- <input v-if="completed" type="checkbox" id="scales" checked> --> <!-- </ul> -->

        <div class="form-check" v-for="todo in todos" :key="todo.name">



            
            <label class="form-check-label" for="flexCheckDefault">{{todo.nameParDefaut}}</label>
            <input class="form-check-input" type="checkbox" id="flexCheckDefault" v-model="todo.completed" checked >
            <strike v-if="todo.completed==true">{{todo.name}}</strike>
            <label class="form-check-label" for="flexCheckDefault" v-if="todo.completed == false">{{todo.name}}</label>
            <button class="btn btn-primary me-md-2" @click=supprimerTodo>X</button>
             
           
        </div>
        
        
    </section>
</template>

<script>
// import { mapActions } from 'vuex';

export default {
    data(){
        return{
            todos:[{
                nameParDefaut:'Déjà Faite',
                name: '',
                completed: false
            }],
            newTodo:''
        }
    },
    methods:{
        // ...mapActions([deleteTodo]),
        addTodo(){
            this.todos.push({
                completed : false,
                name: this.newTodo
            })
            this.newTodo = ''
        },

        supprimerTodo(todo){
            let index = this.todos.indexOf(todo);
            this.todos.splice(index,1)
        }
    }

}
</script>
<style src="./todo.css"></style>
// Source :
/* 
- Cours et tp 
- https://router.vuejs.org/guide/essentials/navigation.html
- https://www.youtube.com/watch?v=SgtS7jWF2O4&list=PLjwdMgw5TTLW-mAtlR46VajrKs4dep3y0&index=11
- https://www.youtube.com/watch?v=5sNXjRE1C-U
- w3school
- https://stackoverflow.com/questions/35459010/vuejs-remove-element-from-lists
*/