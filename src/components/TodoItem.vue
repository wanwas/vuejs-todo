<template>
    <tr v-bind:class="{completed: todo.completed}">
        <td class="tg-baqh">
            <input type="checkbox" v-if="todo.completed" checked  @change="$emit('change-status', index)" >
            <input type="checkbox" v-else:="todo.completed"  @change="$emit('change-status', index)" >
        </td>
        <td class="tg-baqh todo__index">{{index+1}}</td>
        <td class="tg-0lax todo__title">{{todo.title}}</td>
        <td class="tg-baqh todo__remove" v-on:click="$emit('remove-todo', todo.id)">X</td>
    </tr>
</template>

<script>
export default {
    props: ['todo', 'index']
}
</script>

<style scoped>
    .tg  {border-collapse:collapse;border-spacing:0;}
    .tg td{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
    overflow:hidden;padding:10px 5px;word-break:normal;}
    .tg th{border-color:black;border-style:solid;border-width:1px;font-family:Arial, sans-serif;font-size:14px;
    font-weight:normal;overflow:hidden;padding:10px 5px;word-break:normal;}
    .tg .tg-0lax{text-align:left;vertical-align:top}
    td {
        padding: 3px;
    }
    .circle {
        width: 20px;
        height: 20px;
        border-radius: 50%;
    }
    .completed {
        background: rgba(30, 255, 0, 0.11);
    }
    .todo__remove {
        background: rgba(255, 0, 0, 0.459);
        text-decoration: none;
        cursor: pointer;
        display: flex;
        align-items: center;
        justify-content: center;
    }
</style>