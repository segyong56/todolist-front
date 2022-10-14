<template>
    <div>
        <div class="todo-item__box">
            <div class="todo-item" @click="updateData">{{ todoitem.title }}</div>
            <div class="delete-btn" @click="deleteData">X</div>
        </div>
    </div>
</template>

<script>
import axios from 'axios';

export default {
    props: {
        todoitem: Object,
        id: Number
    },
    data() {
        return {

        }
    },
    methods: {
        async deleteData() {
            console.log(this.id)
            const { data } = await axios.get(`http://localhost:8080/board/delete/${this.id}`)

            console.log(data)
        },
        updateData() {
            console.log('hello')
        }
    }

}
</script>

<style scoped>
.todo-item__box {
    display: flex;
    margin: 10px auto;
    padding: 10px;
    width: 60%;
    justify-content: space-between;
    border: 1px solid #ededed;
    border-radius: 10px;
}

.delete-btn {
    font-weight: bold;
}
</style>