<script setup>
import { onBeforeMount, onMounted } from 'vue';
import CarrouselItem from './CarrouselItem.vue';


const props = defineProps([
    "slides"
])


let currentSlide = 0;
let slideInterval = null;

function setCurrentSlide(index) {
    currentSlide = index
}

onMounted(() => {
    slideInterval = setInterval(() => {
       const index = currentSlide < slides.length - 1 ? currentSlide + 1 : 0;
       setCurrentSlide(index)
    }, 3000)
  },
  onBeforeMount(() => {
   clearInterval(slideInterval)
  })
)
</script>

<template>
    <div class="carrousel">
        <div class="carrousel-inner">
            <carrousel-item v-for="(slide, index) in slides" :slide="slide" :key="`item-${index}`"
                :currentSlide="currentSlide" :index="index">
            </carrousel-item>
        </div>
    </div>
</template>
<style scoped>
.carrousel {
    display: flex;
    justify-content: center;
}

.carrousel-inner {
    position: relative;
    width: 900px;
    height: 400px;
    overflow: hidden;
}
</style>