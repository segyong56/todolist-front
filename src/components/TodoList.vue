<template>
    <div>
        <div class="todo-list">
            <TodoItem v-for="(item, id) in todolist" :key="id" :todoitem="item" :id="item.id" />
        </div>
    </div>
</template>

<script>
import TodoItem from './TodoItem.vue';

export default {
    props: {
        todolist: Array
    },
    components: {
        TodoItem
    },
    mounted() {
        console.log(this.todolist)
    }


}
</script>

<style scoped>

</style>