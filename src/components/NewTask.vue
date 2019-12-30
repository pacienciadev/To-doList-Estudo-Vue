<template>
    <div class="new-task">
        <input 
            class="form-element" 
            type="text" 
            v-model="name" 
            @keydown.enter="add" 
            placeholder="Adicionar nova tarefa.">
        <button class="form-element" @click='add'>+</button>
    </div>
</template>
<script>
export default {
    data(){
        return {
            name: ''
        }
    },
    methods: {
        add(){
            this.$emit('taskAdded', { name: this.name })
            this.name = ''
        }
    }
}
</script>
<style>
    .new-task{
        margin: 35px;
    }
    .form-element{
        outline: none;
        font-size: 1.6rem;
        padding: 10px 10px;
        color: #fff;
    }
    input.form-element{
        width: 500px;
        background: rgba(255, 255, 255, 0.295);
        border: 1px solid #ffffff36;
        border-top-left-radius: 5px;
        border-bottom-left-radius: 5px;
    }
    button.form-element{
        background-color: rgb(190, 255, 106);
        border: 1px solid rgb(190, 255, 106);
        border-top-right-radius: 5px;
        border-bottom-right-radius: 5px;
        width: 50px
    }
    
</style>