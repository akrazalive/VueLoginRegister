<template>
  <div class="vue-template">
    <form @submit.prevent="signIn">
      <h3>Sign In</h3>
      <div class="form-group">
        <label>Email address</label>
        <input v-model="email" type="email" class="form-control form-control-lg" />
      </div>
      <div class="form-group">
        <label>Password</label>
        <input v-model="password" type="password" class="form-control form-control-lg" />
      </div>
      <button type="submit" class="btn btn-dark btn-lg btn-block">Sign In</button>
      <p class="forgot-password text-right mt-2 mb-4">
        <router-link to="/forgot-password">Forgot password ?</router-link>
      </p>
      <div class="social-icons">
        <ul>
          <li><a href="#"><i class="fa fa-google"></i></a></li>
          <li><a href="#"><i class="fa fa-facebook"></i></a></li>
          <li><a href="#"><i class="fa fa-twitter"></i></a></li>
        </ul>
      </div>
    </form>
  </div>
</template>

<script>
import axios from 'axios';
import router from '@/router';

export default {
  data() {
    return {
      email: '',
      password: ''
    };
  },
  methods: {
    signIn() {
    alert('called');
      const credentials = {
        email: this.email,
        password: this.password
      };

      // Replace the following URL with your authentication API endpoint
      const authEndpoint = 'https://your-backend-api.com/authenticate';

      axios.post(authEndpoint, credentials)
        .then(response => {
          // If authentication is successful, navigate to the main dashboard page
          if (response.data.success) {
            router.push('/dashboard');
          } else {
            // Show an error message or handle authentication failure
            console.log('Authentication failed.');
          }
        })
        .catch(error => {
          // Handle API call errors
          console.error('Error occurred during authentication:', error);
        });
    }
  }
};
</script>

<style>
/* Your custom CSS styles for the login form can be added here */
</style>
