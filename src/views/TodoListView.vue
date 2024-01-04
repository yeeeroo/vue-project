<script>
import Swal from 'sweetalert2'

export default {
    data() {
        return {
            newTodos: '',
            deadline: '',
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
            let date = new Date().toISOString().split('T');
            // 解構
            const { newTodos, todos, deadline } = this;
            // 讓 新增事項欄位(newTodos) 為空白時，無法新增新事項
            if (!newTodos || !deadline) {
                Swal.fire({
                    title: "警告：尚有空白處",
                    text: "日期或事項尚未填寫完成",
                    icon: "warning",
                    showDenyButton: true,
                    confirmButtonColor: "#3085d6",
                    confirmButtonText: "確認",
                    denyButtonText: `Don't save`,
                    showClass: {
                        popup: `
                    animate__animated
                    animate__fadeInUp
                    animate__faster
                    `
                    },
                    hideClass: {
                        popup: `
                    animate__animated
                    animate__fadeOutDown
                    animate__faster
                    `
                    },
                }).then((result) => {
                    if (result.isConfirmed) {
                        // 抓取 陣列(todos) 裡的最大數id，此id+1後為陣列的下一個id，如果沒有最大數的話則id為1
                        const listId = todos.length ? Math.max(...todos.map(todo => todo.id)) + 1 : 1;
                        // 印出新增的事項
                        todos.push({
                            id: listId,
                            text: newTodos,
                            done: false,
                            currentDate: date[0],
                            deadline: deadline,
                        });
                        // 在印出後，清空新增事項欄位
                        this.newTodos = '';
                        // 將新一筆資料以JSON格式存入sessionStorage
                        sessionStorage.setItem('todos', JSON.stringify(todos));
                        Swal.fire({
                        title: "完成新增",
                        text: "已加入清單",
                        icon: "success"
                    });
                    } else {
                        return;
                    }
                })
            }

        },
        removeTodo(id) {
            Swal.fire({
                title: "是否確認刪除？",
                text: "警告：無法還原此步驟",
                icon: "question",
                showCancelButton: true,
                confirmButtonColor: "#3085d6",
                cancelButtonColor: "#d33",
                confirmButtonText: "確認刪除",
                cancelButtonText: "取消",
                showClass: {
                    popup: `
                    animate__animated
                    animate__fadeInUp
                    animate__faster
                    `
                },
                hideClass: {
                    popup: `
                    animate__animated
                    animate__fadeOutDown
                    animate__faster
                    `
                },
            }).then((result) => {
                if (result.isConfirmed) {
                    const deleteList = this.todos.filter(todo => todo.id !== id);
                    this.todos = deleteList;
                    // 將新一筆資料以JSON格式存入sessionStorage
                    sessionStorage.setItem('todos', JSON.stringify(deleteList));
                    Swal.fire({
                        title: "完成刪除",
                        text: "事項已被刪除",
                        icon: "success"
                    });
                }
            });
        },
    }
}
</script>

<template>
    <form class="border p-2">
        <h1 class="text-3xl px-2 py-1 mb-2">
            待辦清單:
        </h1>
        <div class="px-3">
            <div class="mb-2">
                <span class="text-lg">截止日: </span>
                <input type="date" v-model="deadline" class="border-2">
            </div>
            <div class="mb-2">
                <input type="text" v-model="newTodos" placeholder="新增事項..." class="border-2 px-2 py-1 mr-1">
                <button type="button" @click="addTodos()" class="border-2 px-2 py-1 bg-violet-400 text-white">新增</button>
            </div>
        </div>
        <ul class="px-3 py-2">
            <li v-for=" todo in todos" :key="todo.id" class="text-xl hover:ring-1">
                <input type="checkbox" v-model="todo.done">
                <span :class="{ 'line-through text-sm': todo.done === true }" class="px-2">
                    {{ todo.text }},
                    Deadline: {{ todo.deadline }}
                </span>
                <div class="px-2 pb-2">
                    <span class="text-sm font-light">
                        Record Date: {{ todo.currentDate }}
                    </span>
                    <button type="button" @click="removeTodo(todo.id)" class="float-end text-2xl">
                        <font-awesome-icon :icon="['fas', 'trash-can']" />
                    </button>
                </div>
            </li>
        </ul>
        <!-- 進度條 -->
        <div>

        </div>
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