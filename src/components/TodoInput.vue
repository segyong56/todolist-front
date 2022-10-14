<template>
    <div>
        <div class="todo-input">
            <input type="text" class="input" v-model="todo" />
            <button class="add-btn" @click="postData">추가</button>
        </div>

    </div>
</template>

<script>
import axios from 'axios';

export default {

    data() {
        return {
            todo: '',
        }
    },
    methods: {
        async postData() {
            const board = {
                title: this.todo,
                content: 'content'
            }
            const { data } = await axios.post("http://localhost:8080/board/writedo", board)

            this.todo = ''
            console.log(data)
        },
    }

}
</script>

<style scoped>
.input {
    width: 50%;
    height: 30px;
    border-radius: 5px;
    border: 1px solid #A7A7A7;
}

.add-btn {
    width: 70px;
    height: 35px;
    margin-left: 5px;
    border-radius: 5px;
    border: 1px solid #fff;
    font-size: 18px;
    font-weight: bold;
    background: #ededed;
    color: #a7a7a7;

}
</style>