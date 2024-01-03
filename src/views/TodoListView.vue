<script>
export default {
    data() {
        return{
            newTodos: '',
            todos:[
                {text:'Laundry',done:true,},
                {text:'Grocery',done:true,},
            ]
        }
    },
    methods: {
        addTodos(){
            this.todos.push({text: this.newTodos ,done:false,});
            this.newTodos='';
        }
    },
}
</script>

<template>
    <form class="border p-2">
        <h1 class="text-xl px-2 py-1">
            待辦清單:
        </h1>
        <div class="">
            <input type="text" v-model="newTodos" class="border">
            <button type="button" @click="addTodos()" class="border px-2" >新增</button>
        </div>
        <ul class="px-3 py-2">
            <li v-for=" todo in todos" :key="todo.id" class="px-1">
                <input type="checkbox" class="p-1">
                <span class="px-3">
                    {{ todo.text }}
                </span>
            </li>
        </ul>
        <font-awesome-icon :icon="['fas', 'trash-can']" />
    </form>
</template>

<style></style>