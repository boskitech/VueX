<template>
    <div>
        <h2>Todos</h2>
        <div class="legend">
            <span>
                Double-click to mark as complete
            </span>
            <span>
                <span class="incomplete-box"></span> = Incomplete
            </span>
            <span>
                <span class="complete-box"></span> = Complete
            </span>
        </div>
        <div class="todos">
            <div 
            v-bind:class="{'is-complete':todo.completed}" 
            @dblclick="onDbClick(todo)" 
            class="todo" v-for="todo in allTodos" 
            :key="todo.id"
            >
            {{ todo.title }}
            <i class="fas fa-trash-alt" @click="deleteTodo(todo.id)"></i> 
            </div>
        </div>
    </div>
</template>

<script>
import { mapGetters, mapActions } from 'vuex';

export default {
    name: "Todos",
    methods: {
        ...mapActions(['fetchTodos', 'deleteTodo', 'updateTodo']),
        onDbClick(todo){
            const updTodo = {
                id: todo.id,
                title: todo.title,
                completed: !todo.completed,
            }
            this.updateTodo(updTodo);
        }
    },
    computed: mapGetters(['allTodos']),
    created(){
        this.fetchTodos()
    }
};
</script>

<style>
    .todos{
        display: grid;
        grid-template-columns: repeat(3, 1fr);
        grid-gap: 1em;
    }

    .todo{
        border: 1px solid #ccc;
        background: #41b883;
        padding: 1rem;
        border-radius: 5px;
        text-align: center;
        position: relative;
        cursor: pointer;
    }

    i{
        position: absolute;
        bottom: 10px;
        right:10px;
        color:#fff;
        cursor: pointer;
    }

    .legend{
        display: flex;
        justify-content: space-around;
        margin-bottom: 1rem;
    }

    .complete-box {
        display: inline-block;
        width: 10px;
        height: 10px;
        background: #35494e;
    }

    .incomplete-box {
        display: inline-block;
        width: 10px;
        height: 10px;
        background: #41b883;
    }

    .is-complete{
        background: #35495e;
        color: #fff
    }
</style>