<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import RegisterForm from './RegisterForm.vue'
</script>

<template>
  <AppLayout>
    <template #content>
      <v-container fluid>
        <v-row class="d-flex justify-center">
          <v-col cols="12" sm="8" md="6">
            <RegisterForm />
          </v-col>
        </v-row>
      </v-container>
    </template>
  </AppLayout>
</template>
