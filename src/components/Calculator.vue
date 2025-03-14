<script setup>
import { ref, computed } from 'vue';
import { evaluate } from 'mathjs/number';

const expression = ref('')
const result = computed(() => {
    try {
        return evaluate(expression.value)
    } catch (error) {
        return 'Помилка'
    }
})

function calculate(){
    result.value = evaluate(expression.value)
}

function useForInput(numb){
    expression.value += numb
}
</script>

<template>
    <div class="calculator">
        <div class="input-part">
            <input class="input-for-expression" v-model="expression" placeholder="Enter your expression"/>
            <div class="buttons">
                <div>
                    <el-button type="primary" circle @click="useForInput(1)">1</el-button>
                    <el-button type="primary" circle @click="useForInput(4)">4</el-button>
                    <el-button type="primary" circle @click="useForInput(7)">7</el-button>
                    <el-button type="primary" circle @click="useForInput('(')">(</el-button>
                    </div>
                <div>
                    <el-button type="primary" circle @click="useForInput(2)">2</el-button>
                    <el-button type="primary" circle @click="useForInput(5)">5</el-button>
                    <el-button type="primary" circle @click="useForInput(8)">8</el-button>
                    <el-button type="primary" circle @click="useForInput(0)">0</el-button>
                </div>
                <div>
                    <el-button type="primary" circle @click="useForInput(1)">3</el-button>
                    <el-button type="primary" circle @click="useForInput(4)">6</el-button>
                    <el-button type="primary" circle @click="useForInput(7)">9</el-button>
                    <el-button type="primary" circle @click="useForInput(')')">)</el-button>
                </div>
                <div>
                    <el-button type="primary" circle @click="useForInput('+')">+</el-button>
                    <el-button type="primary" circle @click="useForInput('-')">-</el-button>
                    <el-button type="primary" circle @click="useForInput('*')">*</el-button>
                    <el-button type="primary" circle @click="useForInput('/')">/</el-button>
                </div>
                <el-button type="primary" circle @click="calculate">=</el-button>
            </div>
        </div>
        <div class="result-part">
            <h1 v-text="result"></h1>
        </div>
    </div>
</template>

<style>

.calculator{
    display: flex;
    background-color: rgb(97, 40, 40);
    border-radius: 12px;
}

.input-part{
    background-color: rgb(18, 18, 18);
    margin: 8px;
    border-radius: 12px;
}

.result-part{
    display: flex;
    flex: 1;
    background-color: rgb(18, 18, 18);
    margin: 8px;
    border-radius: 12px;
    padding: 8px;
    color: yellow;
}

.input-for-expression{
    margin: 12px;
    border-radius: 10px;
    border: none;
}

.buttons{
    margin: 12px;
    margin-top: 0px;
    background-color: rgb(18, 18, 18);
}

.buttons_Column1{
    display: flex;
    flex-direction: column;
    justify-content: start;
    align-items: flex-start;
}

.buttons_Column2{
    display: flex;
    flex-direction: column;
}

.buttons_Column3{
    display: flex;
    flex-direction: column;
}

.buttons_Column4{
    display: flex;
    flex-direction: column;
}

.button{
    flex: 1;
    border-radius: 9px;
    border: none;
    cursor: pointer;
}

</style>