<template>
    <div
        @click="$emit('taskStateChanged', task)" 
        class="task"
        :class="stateClass">
        <span @click.stop="$emit('taskDeleted', task)" class="close">X</span>
        <p>{{ task.name }}</p>
    </div>
</template>
<script>
export default {
    props: {
        task: { type: Object, required: true }
    },
    computed: {
        stateClass(){
            return {
                pending: this.task.pending,
                done: !this.task.pending
            }
        }
    }
}
</script>
<style>
    .task {
        box-sizing: border-box;
        width: 350px;
        height: 100px;
        padding: 10px;
        border-radius: 3px;
        font-size: 2rem;
        font-weight: 300;
        cursor: pointer;
        user-select: none;
        display: flex;
        justify-content: center;
        align-items: center;
        position: relative;
    }
    .pending{
        border-left: 12px solid #b73229;
        background-color: #f44336;
    }
    .done{
        color: #ccc;
        border-left: 12px solid #0a8f08;
        background-color: #59af4d;
        text-decoration: line-through;
    }
    .pending .close{
        background-color: #c90f02;
    }
    .done .close{
        background-color: #25a814;
    }
    .close{
        position: absolute;
        right: 10px;
        top: 10px;
        padding: 7px 12px;
        border-radius: 50%;
        font-size: 0.9rem;
        color: #fff;
    }
</style>