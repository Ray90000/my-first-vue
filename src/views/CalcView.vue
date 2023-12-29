<script>
import MyButton from '@/components/customButton/MyButton.vue';

export default {
    components: {
        MyButton,
    },
    data() {
        return {
            numA: 0,
            numB: 0,
            result: 0
        }
    },
    methods: {
        add() {
            if (!this.numA.toString().trim() === '' || !this.numB.toString().trim() === '') return;
            this.result = this.numA + this.numB;

        },
        reduce() {
            this.result = this.numA - this.numB;
        },
        mult() {
            this.result = this.numA * this.numB;
        },
        division() {
            this.result = this.numA / this.numB;
        }

    },
}
</script>
<template>
    <div class="calc">
        計算機
        <div>
            <label>
                數字A:
                <input type="number" v-model="numA">
            </label>
        </div>
        <div>
            <label>
                數字B:
                <input type="number" v-model="numB">
            </label>
        </div>
        <div class="btns">
            <!-- <button class="btn" type="button" @click="add()">+</button> -->
            <MyButton @click="add()">+</MyButton>
            <MyButton @click="reduce()">-</MyButton>
            <MyButton @click="mult()">*</MyButton>
            <MyButton @click="division()">/</MyButton>
        </div>
        <div>
            輸出結果:{{ result }}
        </div>
        <div class="box"></div>
    </div>
</template>

<style lang="scss" scoped>
label {
    input {
        @apply border-black border-[1px] m-2;
    }
}

.btns {
    display: flex;
    gap: 30px;
}

.box {
    @apply w-[300px] h-[300px] bg-[wheat] sm:h-[100px] sm:w-[100px] lg:w-[200px] lg:h-[200px];
}
</style>