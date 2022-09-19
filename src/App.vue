<template>
  <v-app>
    <v-app-bar v-if="$route.path !== '/'" app color="#FFFFFF" dark elevation="3">
      <div class="d-flex align-center" @click="$router.push('/')">
        <v-img alt="Vuetify Logo" class="shrink mr-2" contain src="./assets/adp.png" transition="scale-transition" width="80"/>
      </div>
      <v-spacer/>
      <v-menu offset-y>
        <template v-slot:activator="{ on, attrs }">
          <v-btn v-bind="attrs" v-on="on" text color="#000000" class="text-lowercase font-weight-medium" v-if="$route.path !== '/'">
            <v-icon class="mr-2" color="#EE2722">mdi-account-circle</v-icon>
            <p class="mb-0 font-weight-regular">john.smith</p>
            <v-icon class="ml-2" color="grey">mdi-chevron-down</v-icon>
          </v-btn>
        </template>
        <v-list>
          <v-list-item @click="$router.push('/')">
            <v-list-item-title>Logout</v-list-item-title>
          </v-list-item>
        </v-list>
      </v-menu>
    </v-app-bar>

    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',

  data: () => ({
    //
  })
}
</script>

<style>
  .container {
    max-width: 100% !important;
    background-color: #f6f8fa;
  }
  .v-card {
    border-radius: 8px !important;
  }
</style>
