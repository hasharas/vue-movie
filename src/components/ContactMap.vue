<template>
  <section class="contact-section">
    <div class="container">
      <h2 class="title-left">How to reach us</h2>
      <p class="p-title">Lorem ipsum dolor sit amet, consetetur.</p>

      <div class="split-wrapper">
        <!-- Contact Form -->
        <form @submit.prevent="handleSubmit" novalidate class="form-side">
          <div class="form-row">
            <div class="form-group">
              <label for="firstName">First Name *</label>
              <input id="firstName" type="text" v-model="form.firstName" :class="{ error: errors.firstName }" />
              <span v-if="errors.firstName" class="error-msg">First name is required</span>
            </div>

            <div class="form-group">
              <label for="lastName">Last Name *</label>
              <input id="lastName" type="text" v-model="form.lastName" :class="{ error: errors.lastName }" />
              <span v-if="errors.lastName" class="error-msg">Last name is required</span>
            </div>
          </div>

          <div class="form-group">
            <label for="email">Email *</label>
            <input id="email" type="email" v-model="form.email" :class="{ error: errors.email }" />
            <span v-if="errors.email" class="error-msg">Valid email is required</span>
          </div>

          <div class="form-group">
            <label for="telephone">Telephone</label>
            <input id="telephone" type="text" v-model="form.telephone" />
          </div>

          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" v-model="form.message" :class="{ error: errors.message }"></textarea>
            <span v-if="errors.message" class="error-msg">Message is required</span>
          </div>

          <span class="checkmark">* required field</span>

          <div class="form-check-row">
            <input type="checkbox" v-model="form.terms" id="terms" />
            <label for="terms">I agree to the <u>Terms & Conditions</u></label>
          </div>

          <div class="submit-wrapper">
            <button type="submit">SUBMIT</button>
          </div>
        </form>

        <!-- Map -->
        <div class="map-side">
          <iframe
            src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d3036.1397532154595!2d-3.636301784195986!3d40.44566787936098!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0xd422f5f3c7ae7b5%3A0x60b370b54c5ce398!2sAmadeus%20IT%20Group!5e0!3m2!1sen!2sus!4v1690877721913!5m2!1sen!2sus"
            width="100%"
            height="100%"
            style="border:0;"
            allowfullscreen=""
            loading="lazy"
          ></iframe>
        </div>
      </div>
    </div>
  </section>
</template>

<script>
export default {
  data() {
    return {
      form: {
        firstName: '',
        lastName: '',
        email: '',
        telephone: '',
        message: '',
        terms: false
      },
      errors: {}
    }
  },
  methods: {
    handleSubmit() {
      this.errors = {}

      if (!this.form.firstName) this.errors.firstName = true
      if (!this.form.lastName) this.errors.lastName = true
      if (!this.form.email || !this.validEmail(this.form.email)) this.errors.email = true
      if (!this.form.message) this.errors.message = true

      if (Object.keys(this.errors).length === 0) {
        alert(JSON.stringify(this.form, null, 2))
      }
    },
    validEmail(email) {
      const re = /\S+@\S+\.\S+/
      return re.test(email)
    }
  }
}
</script>


<style scoped>
.contact-section {
  background-color: #000;
  color: #fff;
  padding: 60px 20px 50px;
}

.container {
  max-width: 1200px;
  margin: auto;
}

.title-left {
  font-size: 28px;
  margin-bottom: 20px;
  text-align: left;
}

.p-title {
  font-size: 16px;
  color: #ccc;
  margin-bottom: 25px;
}

.split-wrapper {
  display: flex;
  gap: 40px;
  flex-wrap: wrap;
  justify-content: space-between;
}

.form-side {
  flex: 0 0 40%;
}

.map-side {
  flex: 0 0 50%;
  min-height: 500px;
  position: relative;
}

.form-row {
  display: flex;
  gap: 10px;
  flex-wrap: wrap;
}

.form-group {
  flex: 1;
  margin-bottom: 20px;
  display: flex;
  flex-direction: column;
}

/* Labels above inputs */
.form-group label {
  margin-bottom: 6px;
  font-weight: 600;
  font-size: 14px;
  color: #ccc;
}

input,
textarea {
  width: 100%;
  padding: 10px;
  border: 1px solid #999;
  border-radius: 4px;
  font-size: 16px;
  background: #666; /* gray background */
  color: #fff;
}

textarea {
  height: 100px;
}

input.error,
textarea.error {
  border-color: red;
}

.error-msg {
  color: red;
  font-size: 13px;
  margin-top: 5px;
  display: block;
}

.form-check-row {
  display: flex;
  align-items: center;
  gap: 10px;
  margin: 20px 0;
  font-size: 14px;
}

.form-check-row input[type="checkbox"] {
  width: 20px;
  height: 20px;
  margin: 0;
  flex-shrink: 0;
}

.form-check-row label {
  color: #fff;
  user-select: none;
  cursor: pointer;
}

.form-check-row label u {
  text-decoration: underline;
  cursor: pointer;
}

.submit-wrapper {
  text-align: right;
}

button {
  background-color: #eac805;
  color: #ffffff;
  padding: 10px 25px;
  border: none;
  font-weight: normal;
  cursor: pointer;
  border-radius: 4px;
  width: 50%;
  
}

.footer-info {
  background-color: #444;
  display: flex;
  justify-content: space-between;
  padding: 20px;
  align-items: center;
  margin-top: 60px;
  flex-wrap: wrap;
}

.address-block {
  display: flex;
  align-items: center;
  gap: 10px;
  font-size: 16px;
  color: #fff;
}

.map-pin {
  width: 20px;
}

.social-icons {
  display: flex;
  gap: 15px;
}

.social-icons img {
  width: 28px;
  cursor: pointer;
}

.footer-bottom {
  text-align: center;
  padding: 20px 10px;
  background-color: #444;
  color: #ccc;
  font-size: 14px;
}

.map-pin-overlay {
  position: absolute;
  top: 20px;
  left: 20px;
  width: 30px;
  pointer-events: none;
  z-index: 10;
}

/* Responsive */
@media (max-width: 768px) {
  .split-wrapper {
    flex-direction: column;
  }

  .form-side,
  .map-side {
    width: 100%;
    flex: none;
  }

  .submit-wrapper {
    text-align: left;
  }

  .footer-info {
    flex-direction: column;
    text-align: center;
    gap: 20px;
  }
}
</style>
