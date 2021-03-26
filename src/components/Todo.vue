<template>


    <section class="todoapp">
        <header class="header">
            <h1 class="display-1">Voici ma liste de taches <span class="btn btn-outline-primary">Todo</span></h1>
            <br>
            <h2 class="ajoutTache" for="text">Ajouter une tache</h2>
            <br>
            
            <div class="input-group mb-3">
                <button class="btn btn-outline-secondary" type="button" @click="addTodo">Add</button>
                <input type="text" class="form-control" placeholder="Ajouter une tâche" v-model="newTodo" @keyup.enter=addTodo required>
            </div>
        </header>
        

        <div class="form-check" v-for="todo in todos" :key="todo.name">
           
            <strike class="form-check-label" for="flexCheckDefault">{{todo.nameParDefaut}}</strike>
            <input class="form-check-input" type="checkbox" id="flexCheckDefault" v-model="todo.completed" checked >
            <strike class="str" v-if="todo.completed==true">{{todo.name}}</strike>
            <label class="form-check-label" for="flexCheckDefault" v-if="todo.completed == false">{{todo.name}}</label>
            <button class="badge bg-primary" @click=supprimerTodo>X</button>
             
        </div>
        
        
    </section>
</template>








<script>
// import { mapActions } from 'vuex';

export default {
    name:"Todo",
    data(){
        return{
            todos:[{
                nameParDefaut:'Déjà Faite',
                name: '',
                completed: true
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





<style>@import './todo.css';</style>











// Source :
/* 
- Cours et tp 
- https://router.vuejs.org/guide/essentials/navigation.html
- https://www.youtube.com/watch?v=SgtS7jWF2O4&list=PLjwdMgw5TTLW-mAtlR46VajrKs4dep3y0&index=11
- https://www.youtube.com/watch?v=5sNXjRE1C-U
- w3school
- https://stackoverflow.com/questions/35459010/vuejs-remove-element-from-lists
- https://getbootstrap.com/
*/
