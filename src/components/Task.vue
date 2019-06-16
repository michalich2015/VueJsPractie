<template>
    <div class="task">
        <div >
            <h3 class="task__title" >{{data.title}}</h3>
            <p class="task__desc" >{{data.desc}}</p>
        </div>
            <button class="task__done" @click="deleteToDo(index)">✔</button>

    </div>
</template>
<script>
export default{
    props: ['data'],
    methods:{ 
        deleteToDo(index){
            this.$emit('delete-todo',index);
        }
    }
}
</script>