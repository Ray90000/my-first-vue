<template>
    <div>
        <ul>
            <li v-for="item in items" :key="item.id">
                <span v-if="item.editing">
                    <!-- 編輯模式 -->
                    <input v-model="item.text" />
                    <button @click="saveEdit(item)">保存</button>
                    <button @click="cancelEdit(item)">取消</button>
                </span>
                <span v-else>
                    <!-- 顯示模式 -->
                    {{ item.text }}
                    <button @click="startEdit(item)">編輯</button>
                </span>
            </li>
        </ul>
    </div>
</template>
  
<script>
export default {
    data() {
        return {
            items: [
                { id: 1, text: 'Item 1', editing: false },
                { id: 2, text: 'Item 2', editing: false },
                // ...其他項目
            ]
        };
    },
    methods: {
        startEdit(item) {
            // 啟用編輯模式
            item.editing = true;
        },
        saveEdit(item) {
            // 保存修改
            item.editing = false;
        },
        cancelEdit(item) {
            // 取消編輯
            item.editing = false;
        }
    }
};
</script>
  