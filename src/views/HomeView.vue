<template>
  <v-container class="fill-height py-0">
    <v-row class="fill-height">
      <v-col cols="12" class="col-md-4 col-xl-3 pt-12 px-6 text-center d-flex justify-center">
        <v-col style="max-width: 400px">
          <v-icon size="100" class="mt-8" color="#EE2722">mdi-account-convert-outline</v-icon>
          <h1 class="mt-6">Workforce Certify</h1>
          <p class="mb-12 text--secondary">Welcome back! Please enter your details.</p>
          <v-text-field placeholder="Email" prepend-inner-icon="mdi-email" outlined color="#000"/>
          <v-text-field placeholder="Password" prepend-inner-icon="mdi-lock" outlined color="#000"/>
          <p class="text-right text-decoration-underline font-weight-medium">Forgot Password</p>
          <v-btn color="#EE2722" large class="white--text my-5 px-5 font-weight-bold" style="width: 100%" @click="$router.push('/dashboard')">Login</v-btn>
        </v-col>
      </v-col>
      <v-col class="col-md-8 col-xl-9 pa-0 d-none d-md-block">
        <v-img src="../assets/background.jpg" height="100%"/>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>

export default {
  name: 'HomeView'
}
</script>
