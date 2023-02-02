/**
* v-bind:value="title" привязка инпута к модели
* @input="title = $event.target.value" реализация двухстороннего связывания с моделью
* @click="createPost" отработка метода при собитии клик
* @submit.prevent отмена действия браузера по умолчанию
*/
<template>
    <div class="app">
        <form @submit.prevent>
        <h4>Создание поста</h4>
        <input 
            v-bind:value="title"
            @input="title = $event.target.value" 
            class="input" 
            type="text" 
            placeholder="Название"
            >
        <input 
            v-bind:value="body" 
            @input="body = $event.target.value"
            class="input" 
            type="text" 
            placeholder="Описание"
            >
        <button class="btn" @click="createPost">Создать</button>
        </form>
        <div class="post" v-for="post in posts">
            <div><strong>Название:</strong> {{ post.title }}</div>
            <div><strong>Описание:</strong> {{ post.body }}</div>
        </div>
    </div>
</template>

<script>
    export default {
        data(){
            return{
                posts: [
                    { id: 1, title: 'Пост о java script 1', body: 'java script универсальный ЯП',},
                    { id: 2, title: 'Пост о java script 2', body: 'java script универсальный ЯП',},
                    { id: 3, title: 'Пост о java script 3', body: 'java script универсальный ЯП',},
                ],
                title: '',
                body: '',
            }
        },
        methods: {
            createPost(){
                const newPost = {
                    id: Date.now(),
                    title: this.title,
                    body: this.body,
                }
                this.posts.push(newPost);
                this.title = '';
                this.body = '';
            },
        }
    }
</script>

<style>
* { 
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
.app{
    padding: 20px;
}
form{
    display: flex;
    flex-direction: column;
}
.post{
    padding: 15px;
    border: 2px solid teal;
    margin-top: 15px;
}
.input{
    width: 100%;
    border: 1px solid teal;
    padding: 10px 15px;
    margin-top: 10px;
}
.btn{
    margin-top: 15px;
    align-self: flex-end;
    border: 1px solid teal;
    padding: 10px 15px;
    background: none;
    color: teal;
    transition: 0.3s;
}
.btn:hover{
    background: teal;
    color: white;
    border: 1px solid white;
}
</style>