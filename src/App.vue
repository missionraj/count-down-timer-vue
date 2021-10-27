<script setup lang="ts">
// This starter template is using Vue 3 <script setup> SFCs
// Check out https://v3.vuejs.org/api/sfc-script-setup.html#sfc-script-setup

import Timer from "@/components/Timer.vue";
import { onMounted, onUnmounted, ref } from "vue";

const newYears = "1 Jan 2022";

const daysRemaining = ref("");
const hoursRemaining = ref("");
const minuteRemaining = ref("");
const secondsRemaining = ref("");
const countdown = () => {
    const newYearsDate: Date = new Date(newYears);
    const currentDate: Date = new Date();

    const totalSeconds = (newYearsDate.getTime() - currentDate.getTime()) / 1000;

    const days = Math.floor(totalSeconds / 3600 / 24);
    const hours = Math.floor(totalSeconds / 3600) % 24;
    const mins = Math.floor(totalSeconds / 60) % 60;
    const seconds = Math.floor(totalSeconds) % 60;

    daysRemaining.value = days.toString();
    hoursRemaining.value = formatTime(hours);
    minuteRemaining.value = formatTime(mins);
    secondsRemaining.value = formatTime(seconds);
}

function formatTime(time: number) {
    return time < 10 ? `0${time}` : time.toString();
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
      Until new Beginings 
    </div>
    <div class="timer"> 
        <Timer :count="daysRemaining" label="Days" />
        <Timer :count="hoursRemaining" label="Hours" />
        <Timer :count="minuteRemaining" label="Minutes" />
        <Timer :count="secondsRemaining" label="Seconds" />
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
    display: flex;
    flex-direction: column;
    justify-content: space-around;
  }
  .title { 
    font-size: 4rem;
  }

  .timer { 
    display: flex;
    align-items: center;
    justify-content: space-around;
  }

</style>
