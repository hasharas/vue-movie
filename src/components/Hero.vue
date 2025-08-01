<template>
  <section class="hero">
    <video v-if="showVideo" class="hero-video" autoplay muted loop playsinline>
      <source :src="videoSrc" type="video/mp4" />
      Your browser does not support the video tag.
    </video>

    <img v-else :src="poster" alt="Hero background" class="hero-image" />
  </section>
</template>

<script setup>
import poster from "@/assets/Images/Header Image.jpg";
import videoSrc from "@/assets/Videos/Header Video.mp4";
import { ref, onMounted } from "vue";

const showVideo = ref(true);

onMounted(() => {
  const testVideo = document.createElement("video");
  testVideo.src = videoSrc;
  testVideo.onerror = () => {
    showVideo.value = false;
  };
});
</script>

<style scoped>
.hero {
  position: relative;
  width: 100vw;
  height: 100vh;
  overflow: hidden;
  margin: 0;
  padding: 0;
}

.hero-video,
.hero-image {
  position: absolute;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  object-fit: cover;
  object-position: center;
  display: block;
  z-index: 0;
}

/*respon */

@media (max-width: 1024px) {
  .hero,
  .hero-video,
  .hero-image {
    height: 80vh;
  }
}

@media (max-width: 768px) {
  .hero,
  .hero-video,
  .hero-image {
    height: 70vh;
  }
}

@media (max-width: 480px) {
  .hero,
  .hero-video,
  .hero-image {
    height: 60vh;
  }
}
</style>
