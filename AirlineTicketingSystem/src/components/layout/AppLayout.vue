<script setup></script>

<script></script>

<template>
  <v-responsive>
    <v-app>
      <v-app-bar
        style="background: linear-gradient(#212121, #000000)"
        elevation="8"
        app
        color="primary"
      >
        <v-col class="d-flex align-center"
          ><v-img src="/logo/try2.png" max-width="50"></v-img
          ><v-app-bar-title
            ><span class="font-weight-bold" style="color: #fafafa"
              >AirlineTicketingSystem</span
            ></v-app-bar-title
          ></v-col
        >

        <v-spacer></v-spacer>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>

      <v-main style="background-color: #616161">
        <v-container><slot name="content"></slot> </v-container>
      </v-main>

      <v-footer style="background: linear-gradient(#212121, #000000)" border app class="dflex">
        <v-row justify="center" no-gutters>
          <v-col class="text-center mt-4" cols="12" style="color: #fafafa">
            <strong><p>&copy; 2024 AirlineTicketingSystem. All Rights Reserved.</p></strong>
          </v-col>
        </v-row>
      </v-footer>
    </v-app>
  </v-responsive>
</template>
