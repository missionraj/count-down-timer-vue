<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup

import Timer from "@/components/Timer.vue";
import { onMounted, onUnmounted } from "vue";

const newYears = "1 Jan 2022";
const currentDate : Date = new Date();
const countdown = () => {
    const newYearsDate: Date = new Date(newYears);
    const currentDate: Date = new Date();

    const totalSeconds = (newYearsDate.getTime() - currentDate.getTime()) / 1000;

    const days = Math.floor(totalSeconds / 3600 / 24);
    const hours = Math.floor(totalSeconds / 3600) % 24;
    const mins = Math.floor(totalSeconds / 60) % 60;
    const seconds = Math.floor(totalSeconds) % 60;

    console.log(days, hours, mins, seconds);
}
let timeVar: ReturnType<typeof setInterval> ;
  onMounted(()=> { 
    timeVar = setInterval(countdown, 1000);
  })

  onUnmounted(()=> { 
    clearInterval(timeVar);
  })
</script>

<template>
  <div class="container">
    <div class="title">
      <h1> Until new Beginings </h1>
    </div>
    <div class="timer"> 
        <Timer />
        <Timer />
        <Timer />
        <Timer />
        <Timer />
    </div>
  </div>
</template>

<style>

  @import url('https://fonts.googleapis.com/css2?family=Roboto+Slab&display=swap'); 

  body {
    font-family: 'Roboto Slab', serif;
    margin: 0;
    padding:0;
  }
  .container { 
    height: 100vh;
    background-image: url('@/assets/mountain-rocks.jpg');
    background-attachment: fixed;
    background-size: cover;
    background-position: center center;
    background-repeat: no-repeat;
    text-align: center;
    color: #fff;
  }
  .title { 
    padding-top: 3rem;
  }

  .timer { 
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

</style>
