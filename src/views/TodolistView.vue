<script>
export default {
    data() {
        return {
            addText: '',
            addDateStart: '',
            addDateEnd: '',
            formattedDate: '',
            toDoListArr: [
                {
                    id: 1,
                    toDo: '不要下雨',
                    dateStart: '2024-01-03',
                    dateEnd: '2024-01-04',
                    checkThis: false,
                },
            ],
        }
    },
    //當網頁載入時會觸發
    mounted() {
        //date
        let currentDate = new Date();
        const year = currentDate.getFullYear();
        const month = currentDate.getMonth() + 1;
        const day = currentDate.getDate();
        this.formattedDate = `${year}-${month}-${day}`;

        if (sessionStorage.getItem("todolist")) {
            this.toDoListArr = JSON.parse(sessionStorage.getItem("todolist"));
        }
    },
    methods: {
        addList() {
            console.log(this.formattedDate);
            // const{addText,} = this;
            if (this.addText.toString().trim() === '') return;
            const listId = this.toDoListArr.length ? Math.max(...this.toDoListArr.map(item => item.id)) + 1 : 1;
            this.toDoListArr.push({
                id: listId,
                toDo: this.addText,
                dateStart: this.formattedDate,
                dateEnd: this.addDateEnd,
                checkThis: false,
            })
            this.addText = '';
            //江心的衣料存入session，將資料轉成json格式儲存至session內
            sessionStorage.setItem("todolist", JSON.stringify(this.toDoListArr));

        },
        deleteList(id) {
            const { toDoListArr } = this;
            const deleteList = toDoListArr.filter(item => item.id !== id);
            //如果要修改data直的話,還是要加上this
            this.toDoListArr = deleteList;
            sessionStorage.setItem("todolist", JSON.stringify(deleteList));
            console.log(deleteList);
        }
    }
}
</script>

<template>
    <div class="todolist">
        <div class="td-title">TODOLIST
            <font-awesome-icon :icon="['fas', 'table-list']" />
        </div>
        <div class="td-create">
            <input type="text" v-model="addText">
            <button @click="addList()">
                <font-awesome-icon :icon="['fas', 'plus']" />
            </button>

        </div>
        <div>
            <!-- Start: <input v-model="addDateStart" type="date" class=" border-orange-500 border-[4px]"> -->
            End: <input v-model="addDateEnd" type="date" class=" border-orange-500 border-[4px]">
        </div>
        <div class="td-lists">
            <div class="td-list" v-for="item in toDoListArr" :key="item.id"
                :class="{ 'bg-green-500': item.checkThis === true }">
                <input v-model="item.checkThis" type="checkbox" @click="console.log(item.checkThis)">
                <span>{{ item.toDo }}</span>
                <span>{{ item.dateStart }}-{{ item.dateEnd }}</span>


                <button @click="deleteList(item.id)"><font-awesome-icon :icon="['fas', 'trash']" /></button>
            </div>
        </div>
        <div class="td-apply">
            <div class="tasks">
                <div class="task-25">1</div>
                <div class="task-50">2</div>
                <div class="task-75">3</div>
                <div class="task-100">4</div>
            </div>
            <div class="td-remove">
                <button>Remove</button>
            </div>
        </div>
    </div>
</template>

<style scoped>
.todolist {
    @apply w-[60%] flex flex-col items-center gap-4 p-4 border;

    .td-title {
        @apply text-4xl;
    }

    .td-create {
        input {
            @apply border-orange-500 border-4 h-[50px] w-[400px];
        }




        button {
            @apply bg-gray-500 w-[50px] h-[50px] ml-1 text-white;
        }
    }

    .td-lists {
        @apply border w-[75%] h-[700px] overflow-y-scroll;

        .td-list {
            @apply p-2 border-[2px]  flex justify-center items-center gap-4 ;

            button {
                @apply ml-auto p-3;
            }

            /* .done {
                text-decoration: line-through;
            } */
        }

    }

    .td-apply {
        @apply w-[100%] flex justify-around mt-auto;

        .tasks {
            @apply flex;
        }

        .td-remove {
            @apply border;
        }
    }

}
</style>