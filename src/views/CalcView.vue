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
            result: null,
            calcType : ["+","-","*","/"],
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
        <div class="calc-t">計算機</div>
        <div class="result">
            輸出結果:{{ result }}
        </div>
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
        <div class="calc-btns">
            <MyButton @click="add()">+</MyButton>
            <MyButton @click="reduce()">-</MyButton>
            <MyButton @click="mult()">*</MyButton>
            <MyButton @click="division()">/</MyButton>
        </div>
        <!-- <div class="number-btns">
            <div class="number-btn">1</div>
            <div class="number-btn">2</div>
            <div class="number-btn">3</div>
            <div class="number-btn">4</div>
            <div class="number-btn">5</div>
            <div class="number-btn">6</div>
            <div class="number-btn">7</div>
            <div class="number-btn">8</div>
            <div class="number-btn">9</div>
        </div>
        <div class="result-btn">
            =
        </div> -->
        <!-- <div class="box"></div> -->
    </div>
</template>

<style lang="scss" scoped>
.calc {
    width: 300px;
    // background-color: black;
}

.calc>div {
    margin-top: 20px;
}

.calc-t {
    font-size: 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
    color: aliceblue;
}

// label {
//     input {
//         @apply border-black border-[1px] m-2;
//     }
// }

.calc-btns {
    display: flex;
    justify-content: space-around;
}

// .number-btns {
//     @apply flex flex-wrap;
//     .number-btn {
//         @apply flex justify-center items-center w-[90px] h-[90px]  border-solid rounded-full m-[5px] text-white bg-gray-700 hover:bg-gray-500;
//     }
// }

// .result-btn{
//     @apply flex justify-center items-center w-[100%] h-[60px] bg-[#fb923c] text-white
// }

// .box {
//     @apply w-[300px] h-[300px] bg-[wheat] sm:h-[100px] sm:w-[100px] lg:w-[200px] lg:h-[200px];
// }
</style>