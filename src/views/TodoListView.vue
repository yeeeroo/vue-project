<script>
export default {
    data() {
        return {
            newTodos: '',
            todos: [
                {
                    id: 1,
                    text: 'laundry',
                    done: true,
                },
                {
                    id: 1,
                    text: 'grocery shopping',
                    done: true,
                },
            ]
        }
    },
    methods: {
        addTodos() {
            this.todos.push({ id: this.id++,text: this.newTodos, done: false, });
            this.newTodos = '';
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
            <input type="text" v-model="newTodos" placeholder="新增事項..." class="border px-2">
            <button type="button" @click="addTodos()" class="border px-2">新增</button>
        </div>
        <ul class="px-3 py-2">
            <li v-for=" todo in todos" :key="todo.id" class="px-1">
                <input type="checkbox" class="p-1">
                <span class="px-3">
                    {{ todo.text }}
                </span>
            </li>
        </ul>
        <button type="button" class="px-3 py-2">
            <font-awesome-icon :icon="['fas', 'trash-can']" />
        </button>
    </form>
</template>

<style></style>