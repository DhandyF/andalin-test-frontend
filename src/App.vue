<template>
  <!-- <header>
    <img alt="Vue logo" class="logo" src="@/assets/logo.svg" width="125" height="125" />

    <div class="wrapper">
      <HelloWorld msg="You did it!" />

      <nav>
        <RouterLink to="/">Home</RouterLink>
        <RouterLink to="/about">About</RouterLink>
      </nav>
    </div>
  </header>

  <RouterView /> -->
  <div class="container">
    <div class="navbar">
      <h1>Andalin</h1>
      <RouterLink class="menu" to="/">Welcome</RouterLink>
      <RouterLink class="menu" to="/register">Register</RouterLink>
    </div>
    <!-- <div class="content">
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
    </div> -->
  </div>
  <RouterView />
</template>

<script setup>
import { RouterLink, RouterView } from 'vue-router'
import HelloWorld from './components/HelloWorld.vue'
</script>

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
  width: 100vw;
}

header {
  line-height: 1.5;
  max-height: 100vh;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

nav {
  width: 100%;
  font-size: 12px;
  text-align: center;
  margin-top: 2rem;
}

nav a.router-link-exact-active {
  color: var(--color-text);
}

nav a.router-link-exact-active:hover {
  background-color: transparent;
}

nav a {
  display: inline-block;
  padding: 0 1rem;
  border-left: 1px solid var(--color-border);
}

nav a:first-of-type {
  border: 0;
}

/* @media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }

  nav {
    text-align: left;
    margin-left: -1rem;
    font-size: 1rem;

    padding: 1rem 0;
    margin-top: 1rem;
  }
} */
</style>
