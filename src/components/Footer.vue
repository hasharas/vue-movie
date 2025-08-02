<template>
  <footer class="footer">
    <!-- Top Section -->
    <div class="container">
      <div class="footer-top">
        <div class="address-block">
          <img :src="mapPinIcon" alt="Map Pin" class="map-pin" />
          <h4>Amadeus IT Group</h4>
          <p>
            C. Salvador de Madariaga, 1<br />
            28027 Madrid, Spain
          </p>
        </div>

        <div class="social-follow">
          <span class="follow-label">Follow us on</span>
          <div class="social-icons">
            <img :src="twitterIcon" alt="Twitter" />
            <img :src="youtubeIcon" alt="YouTube" />
          </div>
        </div>
      </div>
    </div>

    <!-- Full-width HR -->
    <hr class="hr" />

    <!-- Bottom Section -->
    <div class="container">
      <div class="footer-bottom">
        <p>Copyright © 2022 Amadeus Hotels. All rights reserved.</p>
        <span>
          Photos by <u>Felix Mooneeram</u> & <u>Serge Kutuzov</u> on <u>Unsplash</u>
        </span>
      </div>
    </div>
  </footer>
</template>

<script>
import Twitter from '@/assets/Icons/Twitter White.svg'
import Youtube from '@/assets/Icons/Youtube White.svg'
import MapPin from '@/assets/Icons/Map Pin Gold.svg'

export default {
  data() {
    return {
      twitterIcon: Twitter,
      youtubeIcon: Youtube,
      mapPinIcon: MapPin
    }
  }
}
</script>

<style scoped>
.footer {
  background-color: #222;
  color: #fff;
  padding: 40px 0 20px;
}

.container {
  max-width: 1200px;
  margin: auto;
  padding: 0 ;
}

/* Top Section */
.footer-top {
  display: flex;
  justify-content: space-between;
  align-items: flex-start;
  flex-wrap: wrap;
  gap: 20px;
}

.address-block {
  display: flex;
  flex-direction: column;
  gap: 10px;
  max-width: 50%;
}

.address-block p {
  font-size: 16px;
  line-height: 1.6;
}

.map-pin {
  width: 20px;
  height: 20px;
}

.social-follow {
  display: flex;
  align-items: center;
  gap: 10px;
  flex-wrap: wrap;
}

.follow-label {
  font-size: 16px;
  color: #ccc;
  white-space: nowrap;
}

.social-icons {
  display: flex;
  gap: 10px;
}

.social-icons img {
  width: 28px;
  cursor: pointer;
  filter: brightness(0) invert(1);
}

/* Full-width HR */
.hr {
  width: 100%;
  border: none;
  height: 1px;
  background-color: #444;
  margin: 20px 0;
}

/* Bottom Section */
.footer-bottom {
  display: flex;
  justify-content: space-between;
  flex-wrap: wrap;
  gap: 10px;
  color: #ccc;
  font-size: 14px;
}

/* Tablet */
@media (max-width: 992px) {
  .address-block {
    max-width: 100%;
  }

  .footer-top {
    flex-direction: column;
    align-items: flex-start;
    gap: 30px;
  }

  .social-follow {
    flex-direction: row;
    align-items: center;
    justify-content: flex-start;
    gap: 15px;
  }

  .footer-bottom {
    flex-direction: column;
    align-items: flex-start;
    gap: 10px;
  }
}

/* Mobile */
@media (max-width: 600px) {
  .footer {
    padding: 30px 0 15px;
  }

  .footer-top {
    align-items: center;
  }

  .address-block,
  .social-follow,
  .footer-bottom {
    text-align: center;
    align-items: center;
    justify-content: center;
    width: 100%;
  }

  .social-follow {
    flex-direction: column;
  }
}
</style>
