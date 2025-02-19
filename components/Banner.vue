<!-- components/ImageSlideshow.vue -->
<template>
    <div class="relative mt-16 sm:mt-40 xl:mx-auto xl:max-w-7xl xl:px-8">
      <!-- Main image container -->
      <div 
        class="relative overflow-hidden xl:rounded-3xl"
        @touchstart="handleTouchStart"
        @touchmove="handleTouchMove"
        @touchend="handleTouchEnd"
      >
        <!-- Image with transitions -->
        <Transition :name="transitionName" mode="out-in">
          <img 
            :key="currentIndex"
            :src="images[currentIndex]" 
            :alt="`Slide ${currentIndex + 1}`"
            class="aspect-[7/3] w-full object-cover transition-all duration-300"
          />
        </Transition>
  
        <!-- Navigation arrows -->
        <button 
          @click="prevSlide"
          class="absolute left-4 top-1/2 -translate-y-1/2 rounded-full bg-white/80 p-2 text-gray-800 shadow-lg transition-all hover:bg-white focus:outline-none focus:ring-2 focus:ring-indigo-500 sm:left-6 md:p-3"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="size-5 md:size-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M15 19l-7-7 7-7" />
          </svg>
        </button>
  
        <button 
          @click="nextSlide"
          class="absolute right-4 top-1/2 -translate-y-1/2 rounded-full bg-white/80 p-2 text-gray-800 shadow-lg transition-all hover:bg-white focus:outline-none focus:ring-2 focus:ring-indigo-500 sm:right-6 md:p-3"
        >
          <svg xmlns="http://www.w3.org/2000/svg" class="size-5 md:size-6" fill="none" viewBox="0 0 24 24" stroke="currentColor">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M9 5l7 7-7 7" />
          </svg>
        </button>
  
        <!-- Progress indicators -->
        <div class="absolute bottom-4 left-1/2 flex -translate-x-1/2 gap-2 sm:bottom-6 md:bottom-8">
          <button
            v-for="(_, index) in images"
            :key="index"
            @click="goToSlide(index)"
            class="h-1.5 rounded-full transition-all sm:h-2"
            :class="[
              currentIndex === index 
                ? 'w-6 bg-white sm:w-8' 
                : 'w-4 bg-white/60 hover:bg-white/80 sm:w-6'
            ]"
            :aria-label="`Go to slide ${index + 1}`"
          />
        </div>
      </div>
  
      <!-- Play/Pause button -->
      <button 
        @click="toggleAutoplay"
        class="absolute bottom-4 right-4 rounded-full bg-white/80 p-2 text-gray-800 shadow-lg transition-all hover:bg-white focus:outline-none focus:ring-2 focus:ring-indigo-500 sm:bottom-6 sm:right-6 md:p-3"
        :aria-label="isPlaying ? 'Pause slideshow' : 'Play slideshow'"
      >
        <svg 
          v-if="isPlaying"
          xmlns="http://www.w3.org/2000/svg" 
          class="size-5 md:size-6" 
          fill="none" 
          viewBox="0 0 24 24" 
          stroke="currentColor"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M10 9v6m4-6v6m7-3a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
        <svg 
          v-else
          xmlns="http://www.w3.org/2000/svg" 
          class="size-5 md:size-6" 
          fill="none" 
          viewBox="0 0 24 24" 
          stroke="currentColor"
        >
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M14.752 11.168l-3.197-2.132A1 1 0 0010 9.87v4.263a1 1 0 001.555.832l3.197-2.132a1 1 0 000-1.664z" />
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M21 12a9 9 0 11-18 0 9 9 0 0118 0z" />
        </svg>
      </button>
    </div>
  </template>
  
  <script setup>
  import { ref, computed, onMounted, onUnmounted } from 'vue'
  
  const props = defineProps({
    images: {
      type: Array,
      required: true,
      validator: (value) => value.length > 0
    },
    autoplayInterval: {
      type: Number,
      default: 5000
    }
  })
  
  const currentIndex = ref(0)
  const isPlaying = ref(true)
  const slideDirection = ref('next')
  const touchStartX = ref(0)
  const touchEndX = ref(0)
  let autoplayTimer = null
  
  // Determine transition name based on direction
  const transitionName = computed(() =>
    slideDirection.value === 'next' ? 'slide-next' : 'slide-prev'
  )
  
  // Navigation functions
  const nextSlide = () => {
    slideDirection.value = 'next'
    currentIndex.value = (currentIndex.value + 1) % props.images.length
    resetAutoplayTimer()
  }
  
  const prevSlide = () => {
    slideDirection.value = 'prev'
    currentIndex.value = currentIndex.value === 0 
      ? props.images.length - 1 
      : currentIndex.value - 1
    resetAutoplayTimer()
  }
  
  const goToSlide = (index) => {
    slideDirection.value = index > currentIndex.value ? 'next' : 'prev'
    currentIndex.value = index
    resetAutoplayTimer()
  }
  
  // Autoplay controls
  const startAutoplay = () => {
    if (isPlaying.value) {
      autoplayTimer = setInterval(nextSlide, props.autoplayInterval)
    }
  }
  
  const stopAutoplay = () => {
    if (autoplayTimer) {
      clearInterval(autoplayTimer)
      autoplayTimer = null
    }
  }
  
  const resetAutoplayTimer = () => {
    stopAutoplay()
    startAutoplay()
  }
  
  const toggleAutoplay = () => {
    isPlaying.value = !isPlaying.value
    if (isPlaying.value) {
      startAutoplay()
    } else {
      stopAutoplay()
    }
  }
  
  // Touch handlers
  const handleTouchStart = (e) => {
    touchStartX.value = e.touches[0].clientX
    touchEndX.value = e.touches[0].clientX
  }
  
  const handleTouchMove = (e) => {
    touchEndX.value = e.touches[0].clientX
  }
  
  const handleTouchEnd = () => {
    const swipeThreshold = 50
    const difference = touchStartX.value - touchEndX.value
  
    if (Math.abs(difference) > swipeThreshold) {
      if (difference > 0) {
        nextSlide()
      } else {
        prevSlide()
      }
    }
  }
  
  // Keyboard navigation
  const handleKeydown = (e) => {
    if (e.key === 'ArrowLeft') {
      prevSlide()
    } else if (e.key === 'ArrowRight') {
      nextSlide()
    }
  }
  
  // Lifecycle hooks
  onMounted(() => {
    startAutoplay()
    window.addEventListener('keydown', handleKeydown)
  })
  
  onUnmounted(() => {
    stopAutoplay()
    window.removeEventListener('keydown', handleKeydown)
  })
  </script>
  
  <style scoped>
  /* Transition for sliding to the next image */
  .slide-next-enter-active,
  .slide-next-leave-active {
    transition: transform 0.3s ease, opacity 0.3s ease;
  }
  .slide-next-enter-from {
    transform: translateX(100%);
    opacity: 0;
  }
  .slide-next-leave-to {
    transform: translateX(-100%);
    opacity: 0;
  }
  
  /* Transition for sliding to the previous image */
  .slide-prev-enter-active,
  .slide-prev-leave-active {
    transition: transform 0.3s ease, opacity 0.3s ease;
  }
  .slide-prev-enter-from {
    transform: translateX(-100%);
    opacity: 0;
  }
  .slide-prev-leave-to {
    transform: translateX(100%);
    opacity: 0;
  }
  </style>
  