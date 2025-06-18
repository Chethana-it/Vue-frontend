<template>
  <section id="contact" class="contact-section">
    <h2 class="section-title">Contact Us</h2>

    <form @submit.prevent="handleSubmit" novalidate>
      <!-- First Name -->
      <div class="form-group">
        <label for="firstName">First Name</label>
        <input
          id="firstName"
          v-model="form.firstName"
          type="text"
          :class="{ 'is-invalid': errors.firstName }"
          placeholder="Enter your first name"
        />
        <div v-if="errors.firstName" class="error">{{ errors.firstName }}</div>
      </div>

      <!-- Last Name -->
      <div class="form-group">
        <label for="lastName">Last Name</label>
        <input
          id="lastName"
          v-model="form.lastName"
          type="text"
          :class="{ 'is-invalid': errors.lastName }"
          placeholder="Enter your last name"
        />
        <div v-if="errors.lastName" class="error">{{ errors.lastName }}</div>
      </div>

      <!-- Email -->
      <div class="form-group">
        <label for="email">Email</label>
        <input
          id="email"
          v-model="form.email"
          type="email"
          :class="{ 'is-invalid': errors.email }"
          placeholder="Enter your email"
        />
        <div v-if="errors.email" class="error">{{ errors.email }}</div>
      </div>

      <!-- Message -->
      <div class="form-group">
        <label for="message">Message</label>
        <textarea
          id="message"
          v-model="form.message"
          :class="{ 'is-invalid': errors.message }"
          placeholder="Type your message"
          rows="4"
        ></textarea>
        <div v-if="errors.message" class="error">{{ errors.message }}</div>
      </div>

      <button type="submit" class="submit-btn">Submit</button>
    </form>

    <!-- Map Embed -->
    <div class="map-container">
      <iframe
        src="https://www.google.com/maps/embed?pb=!1m18!1m12!1m3!1d2023616.6684681047!2d79.38685077701608!3d7.855627709832815!2m3!1f0!2f0!3f0!3m2!1i1024!2i768!4f13.1!3m3!1m2!1s0x3ae2593cf65a1e9d%3A0xe13da4b400e2d38c!2sSri%20Lanka!5e0!3m2!1sen!2slk!4v1750264875081!5m2!1sen!2slk" width="600" height="450" style="border:0;" allowfullscreen="" loading="lazy" referrerpolicy="no-referrer-when-downgrade"
       
      ></iframe>
    </div>
  </section>
</template>

<script>
export default {
  name: 'Contact',
  data() {
    return {
      form: {
        firstName: '',
        lastName: '',
        email: '',
        message: ''
      },
      errors: {}
    }
  },
  methods: {
    validate() {
      this.errors = {}
      if (!this.form.firstName) {
        this.errors.firstName = 'First Name is required'
      }
      if (!this.form.lastName) {
        this.errors.lastName = 'Last Name is required'
      }
      if (!this.form.email) {
        this.errors.email = 'Email is required'
      } else if (!/.+@.+\..+/.test(this.form.email)) {
        this.errors.email = 'Please enter a valid email'
      }
      if (!this.form.message) {
        this.errors.message = 'Message is required'
      }
      return Object.keys(this.errors).length === 0
    },
    handleSubmit() {
      if (this.validate()) {
        // All fields valid → show alert (or other logic)
        alert(
          `Form Submitted:\n` +
          `First Name: ${this.form.firstName}\n` +
          `Last Name:  ${this.form.lastName}\n` +
          `Email:      ${this.form.email}\n` +
          `Message:    ${this.form.message}`
        )
        // Clear form
        this.form = { firstName: '', lastName: '', email: '', message: '' }
      }
    }
  }
}
</script>

<style scoped>
.contact-section {
  padding: 60px 20px;
  background: #f5f5f5;
}
.section-title {
  text-align: center;
  font-size: 2rem;
  margin-bottom: 30px;
  color: #333;
}
.form-group {
  max-width: 500px;
  margin: 0 auto 20px;
}
.form-group label {
  display: block;
  margin-bottom: 6px;
  font-weight: bold;
}
.form-group input,
.form-group textarea {
  width: 100%;
  padding: 10px;
  font-size: 1rem;
  border: 1px solid #ccc;
  border-radius: 4px;
}
.form-group .is-invalid {
  border-color: #e74c3c;
}
.error {
  margin-top: 4px;
  font-size: 0.875rem;
  color: #e74c3c;
}
.submit-btn {
  display: block;
  margin: 20px auto;
  padding: 10px 30px;
  font-size: 1rem;
  color: #fff;
  background: #333;
  border: none;
  border-radius: 4px;
  cursor: pointer;
}
.map-container {
width: 100%; 
  max-width: 800px;
  margin: 40px auto 0;
  border: 2px solid #ddd;
  border-radius: 4px;
  overflow: hidden;
}

.map-container iframe {
  width: 100%;           
  height: 300px;        
  display: block;        
  border: 0;
}
</style>