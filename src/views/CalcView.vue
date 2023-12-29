<script>
export default {
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
            <button class="btn" type="button" @click="add()">+</button>
            <button class="btn" type="button" @click="reduce()">-</button>
            <button class="btn" type="button" @click="mult()">*</button>
            <button class="btn" type="button" @click="division()">/</button>
        </div>
        <div>
            輸出結果:{{ result }}
        </div>
    </div>
</template>

<style lang="scss" scoped>
.btns {
    display: flex;
    gap: 30px;

    .btn {
        padding: 10px 20px;
    }
}
</style>