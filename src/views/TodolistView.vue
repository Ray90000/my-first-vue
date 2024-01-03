<script>
export default {

}
</script>

<template>
    <div class="todolist">
        <div class="td-title">TODOLIST
            <font-awesome-icon :icon="['fas', 'table-list']" />
        </div>
        <div class="td-create">
            <label for="">
                <input type="text">

            </label>
            <button>
                <font-awesome-icon :icon="['fas', 'plus']" />
            </button>
        </div>
        <div class="td-list">
            <label for="">
                <input type="checkbox">
                read the book
            </label>
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
            @apply bg-gray-500 w-[50px] h-[50px] ml-1;
        }
    }

    .td-list {
        @apply border w-[75%];
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

}</style>