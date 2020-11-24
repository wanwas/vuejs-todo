<template>
    <form @submit.prevent="createTodo">
        <input type="text" placeholder="Enter title text" v-model=this.text>
        <input type="submit" value="Add">
    </form>
</template>

<script>
export default {    
    data() {
        return {
            text: ''
        }
    },
    methods: {
        createTodo() {
            if (this.text) {
                const newTodo = {
                    id: Date.now(),
                    title: this.text,
                    completed: false
                }
                this.$emit('create-todo', newTodo)
                this.text = ''; 
            } else {
                alert('Please, enter title text')
            }
        }
    },
}
</script>

<style scoped>
    input[type=text] {
        width: 800px;
        margin-right: 5px;
        padding: 4px;
    }
    input[type=submit] {
        background: rgba(0, 128, 0, 0.486);
        border: none;
        outline: none;
        padding: 6px;
        width: 80px;
    }
    input[type=submit]:hover {
        transform: scale(0.95);
    }
    @media screen and (max-width: 900px) {
        input[type=text] {
            width: 80%;
        }
        form {
            width: 90%;
        }
    }
</style>