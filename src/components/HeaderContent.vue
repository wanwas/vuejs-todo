<template>
    <div class="header">
        <h1>To-Do App</h1>
    </div>
</template>

<script>
export default {
    name: 'HeaderContent',
    components: [

    ],
}
</script>

<style scoped>
    @import url('https://fonts.googleapis.com/css2?family=Big+Shoulders+Stencil+Display:wght@100;300;400;500;600;700;800&display=swap');
    .header {
        font-family: 'Big Shoulders Stencil Display', cursive;
        color: white;
        background-color: rgba(0, 0, 0, 0.747);
        padding-left: 40px;
        font-size: 24px;
    }
    h1 {
        padding: 0;
        margin: 0;
    }
</style>