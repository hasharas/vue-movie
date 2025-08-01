<template>
  <header class="header">
    <div class="logo">
      <img :src="logo" alt="Logo" />
    </div>

    <!-- Desktop nav -->
    <nav class="nav desktop-nav">
      <ul>
        <li><a href="#">HOME</a></li>
        <li><a href="#">OUR SCREENS</a></li>
        <li><a href="#">SCHEDULE</a></li>
        <li><a href="#" class="active">MOVIE LIBRARY</a></li>
        <li><a href="#">LOCATION & CONTACT</a></li>
        <li>
          <button
            class="hamburger-inside"
            @click="toggleSideMenu"
            aria-label="Open menu"
          >
            <img :src="menuIcon" alt="Menu Icon" />
          </button>
        </li>
      </ul>
    </nav>

    <!-- Tablet nav -->
    <nav class="nav tablet-nav">
      <ul>
        <li><a href="#">HOME</a></li>
        <li><a href="#">OUR SCREENS</a></li>
        <li><a href="#">SCHEDULE</a></li>
        <li><a href="#" class="active">MOVIE LIBRARY</a></li>
        <li>
          <button
            class="hamburger-inside"
            @click="toggleSideMenu"
            aria-label="Open menu"
          >
            <img :src="menuIcon" alt="Menu Icon" />
          </button>
        </li>
      </ul>
    </nav>

    <!-- Mobile hamburger -->
    <button
      class="hamburger mobile-hamburger"
      @click="toggleSideMenu"
      aria-label="Open menu"
    >
      <img :src="menuIcon" alt="Menu Icon" />
    </button>

    <!-- Overlay -->
    <div v-if="isSideOpen" class="overlay" @click="closeSideMenu"></div>

    <!-- Side drawer -->
    <aside :class="{ 'side-drawer-open': isSideOpen }" class="side-drawer">
      <button class="close-btn" @click="closeSideMenu" aria-label="Close menu">
        <img :src="closeIcon" alt="Close Icon" />
      </button>
      <ul>
        <li v-if="screenSize === 'mobile'"><a href="#">HOME</a></li>
        <li v-if="screenSize === 'mobile'"><a href="#">OUR SCREENS</a></li>
        <li v-if="screenSize === 'mobile'"><a href="#">SCHEDULE</a></li>
        <li v-if="screenSize === 'mobile'">
          <a href="#" class="active">MOVIE LIBRARY</a>
        </li>
        <li v-if="screenSize !== 'desktop'">
          <a href="#">LOCATION & CONTACT</a>
        </li>
        <li><a href="#">GALLERY</a></li>
      </ul>
    </aside>
  </header>
</template>

<script setup>
import { ref, onMounted, onBeforeUnmount } from "vue";
import logo from "@/assets/Logos/Logo White.svg";
import menuIcon from "@/assets/Icons/Menu White.svg";
import closeIcon from "@/assets/Icons/Close White.svg";

const isSideOpen = ref(false);
const screenSize = ref("desktop");

function toggleSideMenu() {
  isSideOpen.value = !isSideOpen.value;
}
function closeSideMenu() {
  isSideOpen.value = false;
}

function checkScreenSize() {
  const width = window.innerWidth;
  if (width <= 600) screenSize.value = "mobile";
  else if (width <= 900) screenSize.value = "tablet";
  else screenSize.value = "desktop";
}

onMounted(() => {
  checkScreenSize();
  window.addEventListener("resize", checkScreenSize);
});
onBeforeUnmount(() => {
  window.removeEventListener("resize", checkScreenSize);
});
</script>

<style scoped>
.header {
  background: black;
  color: white;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 20px 50px;
  position: relative;
  z-index: 10;
  border-bottom: 1px solid #242323ff;
}

.logo {
  display: flex;
  align-items: center;
  gap: 10px;
}

.nav ul {
  display: flex;
  gap: 30px;
  list-style: none;
  align-items: center;
  margin: 0;
  padding: 0;
}
.nav a {
  text-decoration: none;
  color: white;
  font-size: 14px;
  letter-spacing: 1px;
}
.nav a:hover {
  border-bottom: 2px solid white;
}
.nav a.active {
  font-weight: bold;
  text-decoration: underline;
}

.hamburger-inside {
  background: none;
  border: none;
  cursor: pointer;
  margin-left: 10px;
  padding: 0;
}

.hamburger-inside img {
  width: 20px;
  vertical-align: middle;
}

/* Hide navs initially */
.desktop-nav,
.tablet-nav {
  display: none;
}

/* Show desktop nav on desktop */
@media (min-width: 901px) {
  .desktop-nav {
    display: block;
  }
}

/* Show tablet nav on tablets */
@media (min-width: 601px) and (max-width: 900px) {
  .tablet-nav {
    display: block;
  }
}

/* Show mobile hamburger on mobile */
.mobile-hamburger {
  display: none;
  background: none;
  border: none;
  cursor: pointer;
  padding: 0;
}
.mobile-hamburger img {
  width: 28px;
}

@media (max-width: 600px) {
  .mobile-hamburger {
    display: block;
  }
}

/* Overlay background */
.overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  z-index: 999;
  transition: opacity 0.3s ease-in-out;
}

/* Side drawer styles */
.side-drawer {
  position: fixed;
  top: 0;
  right: -280px;
  width: 280px;
  height: 100%;
  background: black;
  color: white;
  padding: 20px;
  box-shadow: -3px 0 6px rgba(0, 0, 0, 0.7);
  transition: right 0.3s ease-in-out;
  z-index: 1000;
  overflow-y: auto;
}

.side-drawer-open {
  right: 0;
}

.side-drawer ul {
  list-style: none;
  padding: 0;
  margin-top: 40px;
}

.side-drawer li {
  margin-bottom: 20px;
}

.side-drawer a {
  color: white;
  font-size: 16px;
  text-decoration: none;
  letter-spacing: 1px;
}

.side-drawer a.active {
  font-weight: bold;
  text-decoration: underline;
}

/* Close button */
.close-btn {
  position: absolute;
  top: 15px;
  right: 15px;
  background: none;
  border: none;
  cursor: pointer;
}

.close-btn img {
  width: 28px;
}
</style>
