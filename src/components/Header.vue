<template>
  <header class="header">
    <div class="logo">
      <img :src="logo" alt="Logo" />
    </div>
    <nav class="nav" :class="{ open: isMenuOpen }">
      <ul>
        <li><a href="#">HOME</a></li>
        <li><a href="#">OUR SCREENS</a></li>
        <li><a href="#">SCHEDULE</a></li>
        <li><a href="#">MOVIE LIBRARY</a></li>
        <li><a href="#">LOCATION & CONTACT</a></li>
      </ul>
    </nav>
    <div class="hamburger" @click="toggleMenu">
      <img :src="menuIcon" alt="Menu" />
    </div>
  </header>
</template>

<script>
import logo from "@/assets/Logos/Logo White.svg";
import menuIcon from "@/assets/Icons/Menu White.svg";

export default {
  data() {
    return {
      isMenuOpen: false,
      logo,
      menuIcon,
    };
  },
  methods: {
    toggleMenu() {
      this.isMenuOpen = !this.isMenuOpen;
    },
  },
};
</script>

<style scoped>
.header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 16px;
}
.logo img {
  width: 120px;
}
.nav {
  display: flex;
}
.nav ul {
  display: flex;
  list-style: none;
  gap: 20px;
}
.nav a {
  text-decoration: none;
  color: black;
  font-weight: bold;
}
.nav a:hover {
  color: red;
}
.hamburger {
  display: none;
  cursor: pointer;
}
.hamburger img {
  width: 30px;
}

/* Responsive */
@media screen and (max-width: 768px) {
  .nav {
    position: absolute;
    top: 70px;
    right: 0;
    background: white;
    flex-direction: column;
    padding: 20px;
    display: none;
  }
  .nav.open {
    display: flex;
  }
  .hamburger {
    display: block;
  }
}
</style>
