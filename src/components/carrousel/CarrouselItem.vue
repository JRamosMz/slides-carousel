<script setup>

const prop = defineProps([
    "slide",
    "currentSlide",
    "index"

]
)

</script>

<template>
    <div class="carrousel-item">
        <img :src="slide" alt="" v-show="currentSlide === index">
    </div>
</template>

<style scoped>
.carrousel-item {
    position: absolute;
    left: 0;
    right: 0;
    top: 0;
    bottom: 0;
}

</style>