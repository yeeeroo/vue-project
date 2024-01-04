<script>
export default {
    data() {
        return {
            newTodos: '',
            todos: [
                {
                    id: 1,
                    text: 'laundry',
                    done: false,
                },
                {
                    id: 2,
                    text: 'grocery shopping',
                    done: false,
                },
            ]
        }
    },
    // 當網頁載入時觸發
    mounted() {
        // 將sessionStorage裡的JSON格式資料轉檔放回陣列
        if (sessionStorage.getItem('todos')) {
            this.todos = JSON.parse(sessionStorage.getItem('todos'));
        }
    },
    methods: {
        addTodos() {
            // 解構
            let { newTodos, todos } = this;
            // 讓 新增事項欄位(newTodos) 為空白時，無法新增新事項
            if (!newTodos) return;
            // 抓取 陣列(todos) 裡的最大數id，此id+1後為陣列的下一個id，如果沒有最大數的話則id為1
            const listId = todos.length ? Math.max(...todos.map(todo => todo.id)) + 1 : 1;
            // 印出新增的事項
            todos.push({
                id: listId,
                text: newTodos,
                done: false,
            });
            // 在印出後，清空新增事項欄位
            this.newTodos = '';
            // 將新一筆資料以JSON格式存入sessionStorage
            sessionStorage.setItem('todos', JSON.stringify(todos));
        },
    },
}
</script>

<template>
    <form class="border p-2">
        <h1 class="text-xl px-2 py-1">
            待辦清單:
        </h1>
        <div class="px-3 pt-2">
            <input type="text" v-model="newTodos" placeholder="新增事項..." class="border-2 px-2">
            <button type="button" @click="addTodos()" class="border px-2">新增</button>
            <div class="my-1">
                截止日:<input type="date" class="border-2">
                登錄日:<input type="date" class="border-2">
            </div>
        </div>
        <ul class="px-3 py-2">
            <li v-for=" todo in todos" :key="todo.id" class="px-1 text-lg">
                <input type="checkbox" v-model="todo.done" class="p-1">
                <span :class="{ 'line-through text-sm': todo.done === true }" class="px-2">
                    {{ todo.text }}
                </span>
            </li>
        </ul>
        <button type="button" class="px-3 py-2">
            <font-awesome-icon :icon="['fas', 'trash-can']" />
        </button>
    </form>
</template>

<style>
/* import googl font */
@import url('https://fonts.googleapis.com/css2?family=Noto+Sans+TC:wght@100;300;500;700;900&display=swap');

html,
body {
    font-family: 'Noto Sans TC', sans-serif;
}

#app {
    font-family: 'Noto Sans TC', sans-serif;
}
</style>