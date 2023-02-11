<script setup>
import { defineEmits } from 'vue';

const emit = defineEmits(['selectOption'])

const { question } = defineProps(['question'])

const emitSelectedOption = (isCorrect) => {
    emit("selectOption", isCorrect)
}

</script>


<template>
    <div class="question-container">
        <h1 class="question">
           {{ question.text }}
        </h1>
    </div>

    <div class="options-container">
        <div 
            v-for="option in question.options" 
            :key="option.id" 
            class="option" 
            @click="emitSelectedOption(option.isCorrect)"
        >
            <p class="option-label">{{ option.label }}</p>
            <div class="option-value">
                <p>{{ option.text }}</p>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .question-container{
        margin:  20px 0 0 0;
    }

    .question{
        font-size: 40px;
        margin: 0 0 20px 0;
    }

    .option{
        display: flex;
        margin: 0 0 20px 0;
        cursor: pointer;
    }

    .option-label{
        background-color: bisque;
        width: 50px;
        height: 50px;
        font-size: 30px;
        display: flex;
        align-items: center;
        justify-content: center;
    }

    .option-value{
        background-color: rgb(244, 239, 239);
        width: 100%;
        font-size: 30px;
        padding: 0 20px;
    }
</style>