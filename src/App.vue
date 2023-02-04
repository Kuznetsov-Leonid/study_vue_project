/**
* v-bind:value="title" привязка инпута к модели
* @input="title = $event.target.value" реализация двухстороннего связывания с моделью
* @click="createPost" отработка метода при собитии клик
* @submit.prevent отмена действия браузера по умолчанию
*/
<template>
    <div class="app">
        <post-form
            @create="createPost"
        />
        <post-list 
            :posts="posts"
            @remove="removePost"
        />
    </div>
</template>

<script>
    import PostForm from './components/PostForm.vue';
    import PostList from './components/PostList.vue';
    export default {
        components: {
            PostForm, PostList,
        },
        data(){
            return{
                posts: [
                    { id: 1, title: 'Пост о java script 1', body: 'java script универсальный ЯП',},
                    { id: 2, title: 'Пост о java script 2', body: 'java script универсальный ЯП',},
                    { id: 3, title: 'Пост о java script 3', body: 'java script универсальный ЯП',},
                    { id: 4, title: 'Пост о java script 4', body: 'java script универсальный ЯП',},
                ],
            }
        },
        methods: {
            createPost(post){
                this.posts.push(post);
            },
            removePost(post){
                this.posts = this.posts.filter(p => p.id !== post.id)
            }
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
</style>