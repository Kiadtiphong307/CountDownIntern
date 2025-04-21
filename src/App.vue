<script setup>
import { ref, onMounted, onUnmounted } from 'vue'

const Deadline = new Date('2025-05-01T17:00:00Z')

const Daycount = ref(0)
const Hourscount = ref(0)
const Minutescount = ref(0)
const Secondscount = ref(0)

const updateCountdown = () => {
  const now = new Date()
  const timeDifference = Deadline - now

  Daycount.value = Math.floor(timeDifference / (1000 * 60 * 60 * 24))
  Hourscount.value = Math.floor((timeDifference % (1000 * 60 * 60 * 24)) / (1000 * 60 * 60))
  Minutescount.value = Math.floor((timeDifference % (1000 * 60 * 60)) / (1000 * 60))
  Secondscount.value = Math.floor((timeDifference % (1000 * 60)) / 1000)
}

let countdownTimer

onMounted(() => {
  updateCountdown()
  countdownTimer = setInterval(updateCountdown, 1000)
})

onUnmounted(() => {
  clearInterval(countdownTimer)
})
</script>

<template>
  <div class="container mx-auto px-4 py-4">
    <!-- LOGO  -->
    <div class="flex justify-center mt-4 sm:mt-6 md:mt-10 mb-2 md:mb-4">
      <img src="./assets/danger.png" class="w-20 h-20 sm:w-24 sm:h-24 md:w-32 md:h-32" />
    </div>

    <!-- Title -->
    <div class="text-center text-2xl sm:text-4xl md:text-5xl lg:text-6xl font-bold mb-2 md:mb-4">
      <div>COUNT DOWN INTERNSHIP</div>
    </div>

    <!-- Countdown -->
    <div class="text-center mb-4 md:mb-8">
      <div class="text-xl sm:text-2xl md:text-4xl">02 MAY 2025</div>
      <div class="flex flex-wrap justify-center gap-2 md:gap-4 mt-2 md:mt-4">
        <div class="countdown-item">
          <div class="text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-bold">{{ Daycount }}</div>
          <div class="text-xs sm:text-base md:text-2xl">Days</div>
        </div>
        <div
          class="flex items-center text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-bold mx-0 sm:mx-1"
        >
          :
        </div>
        <div class="countdown-item">
          <div class="text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-bold">{{ Hourscount }}</div>
          <div class="text-xs sm:text-base md:text-2xl">Hours</div>
        </div>
        <div
          class="flex items-center text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-bold mx-0 sm:mx-1"
        >
          :
        </div>
        <div class="countdown-item">
          <div class="text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-bold">
            {{ Minutescount }}
          </div>
          <div class="text-xs sm:text-base md:text-2xl">Minutes</div>
        </div>
        <div
          class="flex items-center text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-bold mx-0 sm:mx-1"
        >
          :
        </div>
        <div class="countdown-item">
          <div class="text-4xl sm:text-5xl md:text-6xl lg:text-8xl font-bold">
            {{ Secondscount }}
          </div>
          <div class="text-xs sm:text-base md:text-2xl">Seconds</div>
        </div>
      </div>
    </div>

    <!-- Description -->
    <div class="text-center text-sm sm:text-base md:text-xl mt-4">
      <p>" Good luck Everyone "</p>
    </div>
  </div>
</template>
