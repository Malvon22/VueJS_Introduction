<template>
    <div class="form-to-do form-group">
        <p>
            <input type="text" placeholder="nome" name="author"
            class="form-control" v-model="name">
        </p>
        <p>
            <textarea name="message" class="form-control" placeholder="Cometário" v-model="message"></textarea>
        </p>
        <button v-on:click="addComment" type="submit" class="btn-dark rounded">Comentar</button>
    </div>
</template>
<script>
export default {
    data(){
        return{
            name:'',
            message:''
        }
    },
    methods:{
        addComment(){
            if (this.message.trim() ===''){
                return;
            }

            this.$emit('add-todo',{
                name: this.name,
                message: this.message,
            })

            this.name = '';
            this.message = '';
        }
    }
}
</script>