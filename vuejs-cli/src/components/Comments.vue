<template>
     <div class="container">
        <h1>Comentários</h1>
        <hr />
        <FormToDo v-on:add-todo="addComment"></FormToDo>
        <div class="list-group">
            <p v-if="comments.length <=0">Sem Comentários</p>
            <div class="list-group-item" v-bind:key="comment" v-for="(comment, index) in allComments" >
                <span class="comment_author">Autor: <strong>{{comment.name}}</strong>
                </span>
                <p>{{comment.message}}</p>
                <div>
                    <a href="#" title="Excluir" v-on:click.prevent="removeComment(index)">Excluir</a>
                </div>
            </div>
        </div>
        <hr/>      
    </div>
</template>
<script>
    import FormToDo from './FormToDo';
    export default{
        components:{
            FormToDo
        },
        data() {
            return {
                comments:[
                ]
            }
        },
        methods:{
            addComment(comment){
                this.comments.push(comment)
            },
            removeComment(index){
                this.comments.splice(index, 1);
            }
        },
        computed:{
            allComments(){
                return this.comments.map(comment =>({
                    ...comment,
                    name: comment.name.trim() === '' ? 'Anônimo' : comment.name
                }))
            }
        },
        watch:{
            comments(val){
                console.log(val)
            }
        }
    }
</script>
