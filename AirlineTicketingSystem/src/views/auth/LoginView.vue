<script setup>
import AppLayout from '@/components/layout/AppLayout.vue'
import LoginForm from './LoginForm.vue'
</script>

<template>
    <AppLayout>
      <template #content>
        <v-container fluid>
          <v-row class="d-flex justify-center">
            <v-col cols="12" sm="8" md="6">
              <LoginForm />
            </v-col>
          </v-row>
        </v-container>
      </template>
    </AppLayout>
  </template>