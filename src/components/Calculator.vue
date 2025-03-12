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
                <div class="buttons_Column1">
                    <button class="button" @click="useForInput(1)">1</button>
                    <button class="button" @click="useForInput(4)">4</button>
                    <button class="button" @click="useForInput(7)">7</button>
                    <button class="button" @click="useForInput('(')">(</button>
                    </div>
                <div class="buttons_Column2">
                    <button class="button" @click="useForInput(2)">2</button>
                    <button class="button" @click="useForInput(5)">5</button>
                    <button class="button" @click="useForInput(8)">8</button>
                    <button class="button" @click="useForInput(0)">0</button>
                </div>
                <div class="buttons_Column3">
                    <button class="button" @click="useForInput(1)">3</button>
                    <button class="button" @click="useForInput(4)">6</button>
                    <button class="button" @click="useForInput(7)">9</button>
                    <button class="button" @click="useForInput(')')">)</button>
                </div>
                <div class="buttons_Column4">
                    <button class="button" @click="useForInput('+')">+</button>
                    <button class="button" @click="useForInput('-')">-</button>
                    <button class="button" @click="useForInput('*')">*</button>
                    <button class="button" @click="useForInput('/')">/</button>
                </div>
                <button class="button" @click="calculate">=</button>
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
    font-family: 
        system-ui, 
        -apple-system, 
        BlinkMacSystemFont, 
        'Segoe UI', 
        Roboto, 
        Oxygen, 
        Ubuntu, 
        Cantarell, 
        'Open Sans', 
        'Helvetica Neue', 
        sans-serif;
}

.input-for-expression{
    margin: 12px;
    border-radius: 10px;
    border: none;
}

.buttons{
    display: flex;
    margin: 12px;
    margin-top: 0px;
    background-color: rgb(18, 18, 18);
    gap: 3px;
}

.buttons_Column1{
    display: flex;
    flex-direction: column;
    gap: 3px;
}

.buttons_Column2{
    display: flex;
    flex-direction: column;
    gap: 3px;
}

.buttons_Column3{
    display: flex;
    flex-direction: column;
    gap: 3px;
}

.buttons_Column4{
    display: flex;
    flex-direction: column;
    gap: 3px;
}

.button{
    flex: 1;
    border-radius: 9px;
    border: none;
    font-family: 
        system-ui, 
        -apple-system, 
        BlinkMacSystemFont, 
        'Segoe UI', 
        Roboto, 
        Oxygen, 
        Ubuntu, 
        Cantarell, 
        'Open Sans', 
        'Helvetica Neue', 
        sans-serif;
    cursor: pointer;
}

</style>