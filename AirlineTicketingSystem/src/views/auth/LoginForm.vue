<script setup>
import { ref } from 'vue'
import { useRouter } from 'vue-router'
import axios from 'axios'

const loginEmail = ref('')
const loginPassword = ref('')
const valid = ref(false)
const passwordVisible = ref(false)
const router = useRouter()

const rules = {
  required: value => !!value || 'Required.',
  email: value => /.+@.+\..+/.test(value) || 'E-mail must be valid.',
}

const login = async () => {
  if (valid.value) {
    try {
      const response = await axios.post('/api/login.php', {
        email: loginEmail.value,
        password: loginPassword.value,
      });
      console.log('Response:', response.data);
      router.push('/dashboard'); 
    } catch (error) {
      console.error('Error during login:', error);
    }
  }
}

const togglePasswordVisibility = () => {
  passwordVisible.value = !passwordVisible.value
}

const navigateToSignup = () => {
  router.push('/register ') 
}
</script>

<template>
    <div>
      <v-card class="mx-auto pa-12 pb-8" elevation="8" max-width="448" rounded="lg">
        <div class="text-subtitle-1 text-medium-emphasis">Login</div>
  
        <v-form v-model="valid">
          <v-text-field
            v-model="loginEmail"
            :rules="[rules.required, rules.email]"
            density="compact"
            placeholder="Email address"
            prepend-inner-icon="mdi-email-outline"
            variant="outlined"
          ></v-text-field>
  
          <div class="text-subtitle-1 text-medium-emphasis d-flex align-center justify-space-between">
            Password
            <a class="text-caption text-decoration-none text-blue" href="#" rel="noopener noreferrer" target="_blank">
              Forgot login password?
            </a>
          </div>
  
          <v-text-field
            v-model="loginPassword"
            :append-inner-icon="passwordVisible ? 'mdi-eye-off' : 'mdi-eye'"
            :type="passwordVisible ? 'text' : 'password'"
            density="compact"
            placeholder="Enter your password"
            prepend-inner-icon="mdi-lock-outline"
            variant="outlined"
            @click:append-inner="togglePasswordVisibility"
          ></v-text-field>
  
          <v-btn class="mb-8" color="blue" size="large" variant="tonal" block @click="login">
            Log In
          </v-btn>
  
          <v-card-text class="text-center">
            <a class="text-blue text-decoration-none" @click="navigateToSignup">
              Don't have an account? Sign up now <v-icon icon="mdi-chevron-right"></v-icon>
            </a>
          </v-card-text>
        </v-form>
      </v-card>
    </div>
</template>

<style scoped>
.v-card {
  max-width: 400px;
  margin: 20px auto;
  border-radius: 16px;
  box-shadow: 0 4px 6px -1px rgba(0, 0, 0, 0.1),
              0 2px 4px -2px rgba(0, 0, 0, 0.05);
}

.v-card-title {
  font-size: 22px;
  font-weight: 600;
  color: #1e293b; /* --text-main */
  text-align: center;
  letter-spacing: -0.01em;
}

.v-text-field {
  margin-bottom: 16px;
}

.v-input__control {
  background: #f8fafc; 
  border-radius: 10px;
}

.v-input__slot {
  border: 1px solid #e2e8f0;
  transition: all 0.2s ease;
}

.v-input__slot:hover {
  border-color: #cbd5e1;
}

.v-input__slot:focus-within {
  border-color: #3b82f6; /* --primary */
  box-shadow: 0 0 0 4px rgba(59, 130, 246, 0.1); /* --primary-light */
}

.v-input__prepend-inner {
  color: #64748b; /* --text-secondary */
}

.v-btn {
  border-radius: 10px;
  font-size: 14px;
  font-weight: 500;
}

.v-btn.primary {
  background: #3b82f6; /* --primary */
  color: white;
}

.v-btn.primary:hover {
  background: #2563eb; /* --primary-dark */
  transform: translateY(-1px);
  box-shadow: 0 4px 12px rgba(59, 130, 246, 0.25),
              0 2px 4px rgba(59, 130, 246, 0.15);
}

.v-btn.text {
  color: #64748b; /* --text-secondary */
}

.v-btn.text:hover {
  color: #1e293b; /* --text-main */
}

.v-btn .v-icon {
  color: #64748b; /* --text-secondary */
}

.v-btn .v-icon:hover {
  color: #3b82f6; /* --primary */
}

/* Validation States */
.v-input--is-valid .v-input__slot {
  border-color: #10b981; /* --success */
}

.v-input--is-invalid .v-input__slot {
  border-color: #ef4444; /* Error color */
  animation: shake 0.2s ease-in-out;
}

@keyframes shake {
  0%, 100% {
    transform: translateX(0);
  }
  25% {
    transform: translateX(-4px);
  }
  75% {
    transform: translateX(4px);
  }
}
</style>
