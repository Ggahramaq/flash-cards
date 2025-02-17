<script setup>
import {ref} from 'vue'
const questionNumber = ref(2);
const isQuestion = ref(true);

const questions = [
  { question: "What does HTML stand for?", answer: "HyperText Markup Language.", type: 'HTML' },
  { question: "What is the purpose of the <head> tag in HTML?", answer: "It contains metadata, links to stylesheets, and scripts.", type: 'HTML' },
  { question: "What is the difference between <div> and <span>?", answer: "<div> is a block-level element, while <span> is an inline element.", type: 'HTML' },
  { question: "What is the purpose of the alt attribute in an <img> tag?", answer: "It provides alternative text for screen readers and when the image cannot load.", type: 'HTML' },
  { question: "What is the difference between absolute and relative URLs?", answer: "Absolute URLs include the full web address, while relative URLs are based on the current page’s location.", type: 'HTML' },
  
  { question: "What does CSS stand for?", answer: "Cascading Style Sheets.", type: "CSS" },
  { question: "What is the difference between id and class in CSS?", answer: "id is unique and applies to one element, while class can be used for multiple elements.", type: "CSS" },
  { question: "What is Flexbox in CSS used for?", answer: "It is used to create flexible, responsive layouts.", type: "CSS" },
  { question: "How do you apply a CSS file to an HTML document?", answer: "Using the <link> tag inside the <head> section.", type: "CSS" },
  { question: "What is the difference between relative, absolute, and fixed positioning?", answer: "relative moves an element relative to its normal position, absolute positions it relative to the nearest positioned ancestor, and fixed positions it relative to the viewport.", type: "CSS" },

  { question: "What is JavaScript used for?", answer: "It is used to add interactivity and dynamic behavior to web pages.", type: "JavaScript" },
  { question: "What is the difference between == and === in JavaScript?", answer: "== checks for value equality with type conversion, while === checks for both value and type equality.", type: "JavaScript" },
  { question: "What is an event listener in JavaScript?", answer: "It is a function that waits for user actions like clicks or key presses.", type: "JavaScript" },
  { question: "What is a JavaScript function?", answer: "A reusable block of code that performs a specific task.", type: "JavaScript" },
  { question: "How do you declare a variable in JavaScript?", answer: "Using var, let, or const.", type: "JavaScript" },

  { question: "What is a JavaScript framework?", answer: "A pre-written set of JavaScript libraries that help developers build web applications faster.", type: "Frameworks"},
  { question: "Name three popular JavaScript frameworks.", answer: "React, Angular, Vue.js.", type: "Frameworks"},
  { question: "What is JSX in React?", answer: "JSX is a syntax extension for JavaScript that looks similar to HTML and is used in React components.", type: "Frameworks"},
  { question: "What is the purpose of the v-model directive in Vue.js?", answer: "It creates two-way data binding between an input field and a Vue component.", type: "Frameworks"},
  { question: "How does Angular use TypeScript?", answer: "Angular is built using TypeScript, which adds static typing and additional features to JavaScript.", type: "Frameworks"}
];

const PreviousBtn = () => {
    if (questionNumber.value > 1) {
        questionNumber.value--;
        console.log(questionNumber.value)
        isQuestion.value = true;
    }
}

const NextBtn = () => {
    if (questionNumber.value < 20) {
        questionNumber.value++;
        console.log(questionNumber.value)
        isQuestion.value = true;
    }
}

const toggleAnswer = () => {
    isQuestion.value = !isQuestion.value
}

</script>

<template>
    <div class="flex items-center justify-center min-h-screen">
        <div class="absolute mb-150 text-5xl text-left w-200">Flash Cards: {{ questions[questionNumber - 1].type }}</div>
        <div class="flex absolute mb-120 w-200 h-10 border border-zinc-400 rounded-lg">
            <div class="flex h-8 bg-zinc-400 rounded-lg ml-0.5 transition-all duration-400 ease-out" :style="`width: ${questionNumber*36.3}px; margin-top: 3px;`">
                <div class="flex justify-end items-center w-full mr-1 mt-1 text-white " style="margin-bottom: 2px;">
                    {{ questionNumber*100/20 + "%"}}
                </div>
            </div>
            <div class="absolute right-1 text-black" style="margin-top: 7.5px;">
                {{ questionNumber + " of 20"}}
            </div> 
        </div>
        <div class="question mt-5 border w-200 border-zinc-400 rounded-md">
            <div class="bg-zinc-200 w-198 ml-1 h-98 mt-1 flex items-center justify-center text-center rounded-lg">
                <h1 v-if="isQuestion" class="max-w-100 text-4xl">{{ questions[questionNumber - 1].question }}</h1>
                <h1 v-else class="max-w-220 text-2xl">{{  questions[questionNumber - 1].answer  }}</h1>
            </div>
            <div class="bg-zinc-200 mt-1 h-10 w-198 ml-1 mb-1 justify-between px-2 flex rounded-md">
                <button @click="PreviousBtn" class="text-zinc-500 cursor-pointer inline-flex text-left text-3xl transition duration-300 ease-out hover:text-black">< Previous</button>
                <button v-if="isQuestion" @click="toggleAnswer" class="cursor-pointer inline-flex mr-10 text-3xl text-center">Show Answer</button>
                <button v-else @click="toggleAnswer" class="cursor-pointer text-3xl inline-flex mr-10 text-center">Hide Answer</button>
                <button class="text-zinc-500 cursor-pointer text-3xl inline-flex text-right transition duration-300 ease-out hover:text-black" @click="NextBtn">Next ></button>
            </div>
        </div>
    </div>
</template>

