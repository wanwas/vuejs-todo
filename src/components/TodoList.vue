<template>
    <div class="content">
        <TodoCreate @create-todo="createTodo" />
        <hr>
        <div class="todo__content">
            <table class="todolist">
                <TodoItem @remove-todo="removeTodo" @change-status="changeStatus" v-for:="(item, index) in todos" v-bind:todo="item" v-bind:index="index"/>
            </table>
        </div>
    </div>
</template>

<script>
import TodoItem from '@/components/TodoItem'
import TodoCreate from '@/components/TodoCreate'
export default {
    props: ['todos'],
    name: "TodoList",
    components: {
        TodoItem,
        TodoCreate
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id)
        },
        createTodo(newTodo) {
            this.$emit('create-todo', newTodo)
        },
        changeStatus(index) {
            this.$emit('change-status', index)
        }
    }
}
</script>

<style scoped>
    .content {

        display: flex;
        flex-direction: column;
        align-items: center;
        padding-top: 10px;
    }
    .todo__content {
        max-height: calc(100vh - 120px);

        overflow-y: scroll;
    }
    .todolist {
        width: 900px;
        height: 20px;
    }
    @media screen and (max-width: 900px) {
        .todolist {
            width: 100%;
        }
    }
</style>