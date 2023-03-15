<script setup>
import { ref, onMounted } from 'vue';
const slideIndex = ref(1);

onMounted(() => {
  showSlides(slideIndex.value);
});

function plusSlides(n) {
  showSlides(slideIndex.value += n);
}

function currentSlide(n) {
  showSlides(slideIndex.value = n);
}

function showSlides(n) {
  let i;
  let slides = document.getElementsByClassName("mySlides");
  let dots = document.getElementsByClassName("dot");
  if (n > slides.length) {slideIndex.value = 1}    
  if (n < 1) {slideIndex.value = slides.length}
  for (i = 0; i < slides.length; i++) {
    slides[i].style.display = "none";  
  }
  for (i = 0; i < dots.length; i++) {
    dots[i].className = dots[i].className.replace(" active", "");
  }
  slides[slideIndex.value-1].style.display = "block";  
  dots[slideIndex.value-1].className += " active";
}
</script>

<template>
  <div class="content">
    <div class="slideshow-container">

      <div class="mySlides fade">
        <img src="@/assets/bg-1.jpg" style="width:100%">
        <div class="text">Welcome to this page</div>
      </div>

      <div class="mySlides fade">
        <img src="@/assets/bg-2.jpg" style="width:100%">
        <div class="text">This is slide 2</div>
      </div>
    </div>
    <div style="text-align:center">
      <span class="dot" @click="currentSlide(1)"></span> 
      <span class="dot" @click="currentSlide(2)"></span>
    </div>
  </div>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
}

.navbar {
  display: flex;
  flex-direction: row;
  background-color: transparent;
  width: 100vw;
  padding: 10px 30px;
  position: absolute;
  top: 0;
  z-index: 1;
  color: black;
}

.menu {
  display: flex;
  margin: 0px 20px;
  padding-top: 10px;
  align-content: center;
  text-align: center;
  color: #000 !important;
}

.content {
  display: flex;
  flex-direction: column;
  width: 100vw;
  height: 100vh;
  background-image: url('./assets/bg-1');
}

.mySlides {display: none}

/* Fading animation */
.fade {
  animation-name: fade;
  animation-duration: 1.5s;
}

/* Slideshow container */
.slideshow-container {
  width: 100vw;
  position: relative;
}

/* Caption text */
.text {
  color: #f2f2f2;
  font-size: 15px;
  padding: 8px 12px;
  position: absolute;
  bottom: 50vh;
  width: 100%;
  text-align: center;
}

/* The dots/bullets/indicators */
.dot {
  cursor: pointer;
  height: 15px;
  width: 15px;
  margin: 0 2px;
  background-color: #bbb;
  border-radius: 50%;
  display: inline-block;
  transition: background-color 0.6s ease;
}

.active, .dot:hover {
  background-color: #717171;
}

@keyframes fade {
  from {opacity: .4} 
  to {opacity: 1}
}

/* On smaller screens, decrease text size */
@media only screen and (max-width: 300px) {
  .prev, .next,.text {font-size: 11px}
}

img {
  vertical-align: middle;
  max-width: 100vw;
  height: 100vh;
}

</style>