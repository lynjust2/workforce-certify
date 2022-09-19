<template>
  <v-container class="fill-height align-start">
    <v-row justify="center" class="fill-height">
      <v-col class="contentCol">
        <v-card elevation="0" class="fill-height d-flex flex-column px-2">
          <p class="red--text text-decoration-underline font-weight-medium pt-6 pl-4" @click="$router.push('/dashboard')">
            <v-icon class="mr-2">mdi-arrow-left</v-icon>Back to Dashboard
          </p>
          <v-card-title>I9 Verification Form (Section 1)</v-card-title>
          <v-stepper v-model="e1" alt-labels elevation="0">
            <v-stepper-header>
              <v-stepper-step color="#EE2722" :complete="e1 > 1" step="1">My Information</v-stepper-step>
              <v-divider/>
              <v-stepper-step color="#EE2722" :complete="e1 > 2" step="2">Residency</v-stepper-step>
              <v-divider/>
              <v-stepper-step color="#EE2722" :complete="e1 > 3" step="3">Preparer</v-stepper-step>
              <v-divider/>
              <v-stepper-step color="#EE2722" step="4">Review</v-stepper-step>
            </v-stepper-header>

            <v-stepper-items class="px-0 px-sm-10">
              <v-stepper-content step="1">
                <h2 class="text-center mb-4">My Information</h2>
                <p><strong class="red--text">*</strong> All fields are mandatory unless stated otherwise</p>
                <v-card class="mb-12" elevation="0">
                  <v-container fluid class="overflow-y-auto" style="background-color: #FFFFFF">
                    <v-row>
                      <v-col cols="12" sm="6">
                        <v-text-field color="#000" label="First name" required outlined></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-text-field color="#000" label="Last name" required outlined></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-textarea color="#000" outlined>
                          <template v-slot:label><div>Bio <small>(optional)</small></div></template>
                        </v-textarea>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-select color="#000" label="Favorite animal" required outlined></v-select>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-slider color="#000" label="Age" hint="Be honest" min="1" max="100" thumb-label></v-slider>
                      </v-col>
                      <v-col cols="12">
                        <v-checkbox color="#EE2722">
                          <template v-slot:label>
                            <div @click.stop="">Do you accept the<a href="#">terms</a>and<a href="#">conditions?</a></div>
                          </template>
                        </v-checkbox>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-text-field color="#000" label="First name" required outlined></v-text-field>
                      </v-col>
                      <v-col cols="12" sm="6">
                        <v-text-field color="#000" label="Last name" required outlined></v-text-field>
                      </v-col>
                      <v-col cols="12">
                        <v-textarea color="#EE2722" outlined>
                          <template v-slot:label><div>Bio <small>(optional)</small></div></template>
                        </v-textarea>
                      </v-col>
                    </v-row>
                  </v-container>
                </v-card>
              </v-stepper-content>
              <v-stepper-content step="2">
                <v-card class="mb-12" color="grey lighten-1" height="200px"></v-card>
              </v-stepper-content>
              <v-stepper-content step="3">
                <v-card class="mb-12" color="grey lighten-1" height="200px"></v-card>
              </v-stepper-content>
              <v-stepper-content step="4">
                <v-card class="mb-12" color="grey lighten-1" height="200px"></v-card>
              </v-stepper-content>
            </v-stepper-items>
          </v-stepper>
          <v-spacer/>
          <v-divider/>
          <v-card-actions class="pa-5">
            <v-spacer/>
            <v-btn color="#EE2722" class="white--text mx-5" @click="nextSection">
              {{ e1 < 4 ? 'Save & Continue' : 'Submit' }}
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'FormView',
  data: () => ({
    e1: 1
  }),
  methods: {
    nextSection () {
      if (this.e1 < 4) {
        this.e1 += 1
      } else {
        this.$router.push('/dashboard')
      }
    }
  }
}
</script>

<style scoped>
  .v-stepper__header {
    box-shadow: none;
  }
  .contentCol {
    padding-top: 40px;
    padding-bottom: 40px;
    max-width: 1200px;
  }

</style>
