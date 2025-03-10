<script setup>
import { ref, computed } from 'vue';
import { evaluate } from 'mathjs/number';

const expression = ref('')
const result = computed(() => {
    try {
        console.log(expression.value)
        return evaluate(expression.value)
    } catch (error) {
        return 'Помилка'
    }
})

function calculate(){
    result.value = evaluate(expression.value)
}

function useForInput(numb){
    console.log(numb)
}
</script>

<template>
    <div class="calculator">
        <input class="input-for-digits" v-model="expression" placeholder="Enter your expression"/>
        <div class="digit-buttons">
            <div>
                <button class="digits" @click="useForInput(1)">1</button>
                <button class="digits" @click="useForInput(2)">2</button>
                <button class="digits" @click="useForInput(3)">3</button>
                <button class="action-buttons">+</button>
                <button class="action-buttons">-</button>
                <button class="action-buttons">*</button>
                <button class="action-buttons">/</button>
            </div>
            <div>
                <button class="digits" @click="useForInput(4)">4</button>
                <button class="digits" @click="useForInput(5)">5</button>
                <button class="digits" @click="useForInput(6)">6</button>
            </div>
            <div>
                <button class="digits" @click="useForInput(7)">7</button>
                <button class="digits" @click="useForInput(8)">8</button>
                <button class="digits" @click="useForInput(9)">9</button>
            </div>
            <button class="digits" @click="useForInput()">(</button>
            <button class="digits" @click="useForInput(0)">0</button>
            <button class="digits" @click="useForInput()">)</button>
            <button class="equal-button" @click="calculate">=</button>
        </div>
    </div>
    <p v-text="result"></p>
</template>

<style>

.input-for-digits{
    margin: 12px;
}

.calculator{
  display: flow-root;
  background-color: rgb(97, 40, 40);
  border-radius: 12px;
}

.action-buttons{
    margin-left: 2px;
}

.equal-button{
    margin: 8px;
    width: 95px;
    border: none;
    border-radius: 12px;
    background-color: rgb(240, 229, 231);
    font-weight: bold;
    cursor: pointer;
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

.digit-buttons{
    margin: 12px;
    margin-right: 0px;
    margin-top: 0px;
}

.digits{
    margin: 2px;
    border-radius: 8px;
    border: none;
    background-color: rgb(240, 229, 231);
    font-weight: bold;
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