<template>
    <section class="contact-section">
      <div class="contact-content">
        <h2>Contact Us</h2>
        <p>
          Have any questions or feedback? Reach out to us, and we’ll get back to you as soon as possible.
        </p>
        <form @submit.prevent="submitForm">
          <div class="form-group">
            <label for="name">Name</label>
            <input type="text" id="name" v-model="formData.name" required />
          </div>
          <div class="form-group">
            <label for="email">Email</label>
            <input type="email" id="email" v-model="formData.email" required />
          </div>
          <div class="form-group">
            <label for="subject">Subject</label>
            <input type="text" id="subject" v-model="formData.subject" required />
          </div>
          <div class="form-group">
            <label for="message">Message</label>
            <textarea id="message" v-model="formData.message" rows="4" required></textarea>
          </div>
          <button type="submit" class="submit-btn">Send Message</button>
        </form>
      </div>
    </section>
  </template>
  
  <script>
  export default {
    name: "Contact_Us",
    data() {
      return {
        formData: {
          name: "",
          email: "",
          subject: "",
          message: "",
        },
      };
    },
    methods: {
      submitForm() {
        console.log("Form Data:", this.formData);
        alert("Message sent successfully!");
        // Clear the form
        this.formData.name = "";
        this.formData.email = "";
        this.formData.subject = "";
        this.formData.message = "";
      },
    },
  };
  </script>
  
  <style scoped>
  .contact-section {
    padding: 3rem 2rem;
    background-color: #e6e6fa;
    border-radius: 12px;
    box-shadow: 0 4px 12px rgba(0, 0, 0, 0.1);
    max-width: 800px;
    margin: 2rem auto;
  }
  
  .contact-content {
    text-align: center;
  }
  
  h2 {
    font-size: 2.2rem;
    color: #4e4537;;
    margin-bottom: 1rem;
  }
  
  p {
    font-size: 1rem;
    color:  #4e4537;;
    margin-bottom: 2rem;
  }
  
  form {
    display: flex;
    flex-direction: column;
    gap: 1.5rem;
  }
  
  .form-group {
    display: flex;
    flex-direction: column;
    text-align: left;
  }
  
  label {
    font-size: 1rem;
    color: #4e4537;;
    margin-bottom: 0.5rem;
  }
  
  input,
  textarea {
    padding: 0.75rem;
    font-size: 1rem;
    border: 1px solid #ddd;
    border-radius: 8px;
    outline: none;
    transition: border-color 0.3s ease;
  }
  
  input:focus,
  textarea:focus {
    border-color: #008765;
  }
  
  .submit-btn {
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
    color: #fff;
    background-color: #008765;
    border: none;
    border-radius: 8px;
    cursor: pointer;
    transition: background-color 0.3s ease;
  }
  
  .submit-btn:hover {
    background-color: #008765;
  }
  </style>
  