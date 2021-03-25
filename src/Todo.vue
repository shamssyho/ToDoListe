<template>
    <section class="todoapp">
        <header class="header">
            <h1>Voici ma liste de taches <span class="btn btn-outline-primary">Todo</span></h1>
            <br>
            <!-- <label for="text">Ajouter une tache</label>--> <!-- <input type="text" class="todo">  -->
            
            <div class="input-group mb-3">
                <button class="btn btn-outline-secondary" type="button" @click="addTodo">Add</button>
                <input type="text" class="form-control" placeholder="Ajouter une tâche" v-model="newTodo" @keyup.enter=addTodo required>
            </div>
        </header>
        
        <!-- <ul class="list-group" v-for="todo in todos" :key="todo.name"> <li class="list-group-item" v-on:remove="todos.splice(index, 0)"> {{todo.name}}</li>  <div> --> <!-- <label class="list-group-item">{{todo.name}}</label> --> <!-- <li class="list-group-item"> {{todo.name}}</li> --> <!-- </div> --> <!-- <input v-if="completed" type="checkbox" id="scales" checked> --> <!-- </ul> -->

        <div class="form-check" v-for="(todo, index) in todos" :key="todo.name">
            
            <label class="form-check-label" for="flexCheckDefault">{{todo.nameParDefaut}}</label>
            <input class="form-check-input" type="checkbox" v-on:click="check" value="" id="flexCheckDefault" checked >
             <!-- <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault" > -->
            <label class="form-check-label" for="flexCheckDefault" >{{todo.name}}</label>
             <button v-bind:content="todo" v-on:remove="todos.splice(index, 1)">X</button>
             
           
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
                completed : true,
                name: this.newTodo
            })
            this.newTodo = ''
        },
        check(){
            
            alert('bonjour')
        }
    //     del (index) {
    //   // this.arr.splice(index, 1)
    //   this.myArr.splice(2, 1, 'strawberry');
    // }
        // supprimer(){
        //     this.todos.$remove({
        //         completed = false
        //     });
        // }
    }

}
</script>
<style src="./todo.css"></style>