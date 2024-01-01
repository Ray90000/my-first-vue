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
            result: null
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
        <!-- <div>
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
        </div> -->
        <div class="calc-btns">
            <MyButton @click="add()">+</MyButton>
            <MyButton @click="reduce()">-</MyButton>
            <MyButton @click="mult()">*</MyButton>
            <MyButton @click="division()">/</MyButton>
        </div>
        <div class="number-btns">
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
        <!-- <div class="box"></div> -->
    </div>
</template>

<style lang="scss" scoped>

.calc{
    width: 300px;
}
.calc > div{
    margin-top: 20px;
}
.calc-t{
    font-size: 2rem;
    display: flex;
    justify-content: center;
    align-items: center;
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

.number-btns{
    display: flex;
    flex-wrap: wrap;
    .number-btn{
        display: flex;
        justify-content: center;
        align-items: center;
        width: 90px;
        height: 90px;
        border: 1px solid black;
        border-radius: 50%;
        margin: 5px;
        @apply bg-slate-400 ;
    }
}

// .box {
//     @apply w-[300px] h-[300px] bg-[wheat] sm:h-[100px] sm:w-[100px] lg:w-[200px] lg:h-[200px];
// }
</style>