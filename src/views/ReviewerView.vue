<template>
  <v-container class="fill-height align-start">
    <v-row v-if="!review" justify="center">
      <v-col class="contentCol">
        <h1>Welcome, John Smith!</h1>
        <v-card elevation="0" class="my-10">
          <v-card-title>Overview</v-card-title>
          <v-card-subtitle>Please review the checklist below to complete any assigned tasks related to your I9 verification check.</v-card-subtitle>
          <v-divider/>
          <v-card-text>
            <v-row>
              <v-col>
                123
                Forms to Review
              </v-col>
              <v-divider vertical/>
              <v-col>
                203
                Completed
              </v-col>
            </v-row>
          </v-card-text>
        </v-card>

        <v-card elevation="0" class="my-10">
          <v-card-title>Submitted Forms</v-card-title>
          <v-card-subtitle>As we are evaluating your form, we may contact you to provide additional information. In
            this case, you will receive a notification with instructions.
          </v-card-subtitle>
          <v-card-text>
            <v-divider/>
            <v-data-table :headers="headers" :items="active" disable-sort @click:row="review=true">
              <template v-slot:[`item.status`]="{ item }">
                <v-chip :color="item.status === 'Complete' ? 'green' : 'warning'" class="font-weight-bold white--text">
                  {{ item.status }}
                </v-chip>
              </template>
              <template v-slot:[`item.action`]="{ }">
                <v-btn small depressed color="green" class="white--text">Review</v-btn>
              </template>
            </v-data-table>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>

    <v-row v-else justify="center" class="fill-height">
      <v-col class="contentCol">
        <v-card elevation="0" class="d-flex flex-column px-2">
          <p class="red--text text-decoration-underline font-weight-medium pt-6 pl-4" @click="review=false">
            <v-icon class="mr-2">mdi-arrow-left</v-icon>Back to Dashboard
          </p>
          <v-card-title>I9 Verification Form (#IF99129382)</v-card-title>
          <v-card-subtitle>Submitted 2 Days Ago</v-card-subtitle>
          <v-tabs v-model="applicationTab" color="#EE2722">
            <v-tab>Section 1 (Submission)</v-tab>
            <v-tab>Section 2</v-tab>
          </v-tabs>
          <v-divider/>
          <v-card-text v-if="applicationTab === 0" class="black--text mt-5">
            <h2 class="mb-5">Submission Details</h2>
            <h4>Name</h4>
            <p>John Smith</p>
            <h4>Address</h4>
            <p class="mb-0">123 StreetName Ave</p>
            <p class="mb-0">Toronto, ON 123456</p>
            <p>Canada</p>
            <h4>Email</h4>
            <p>John.smith@emai.com</p>
            <h4>Phone</h4>
            <p>+1 (416) 555-1234 (Personal Primary)</p>
          </v-card-text>
          <v-card-text v-else class="black--text mt-5">
            <h2 class="text-center mb-4">I9 Verification - Section 2</h2>
            <p><strong class="red--text">*</strong> Indicates a required field</p>
            <v-container fluid style="background-color: #FFFFFF">
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
          </v-card-text>
          <v-spacer/>
          <v-divider/>
          <v-card-actions class="py-3">
            <v-spacer/>
            <v-btn color="#EE2722" class="white--text mx-5" @click="nextSection">
              {{ applicationTab < 1 ? 'Review' : 'Submit' }}
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'ReviewerView',
  data: () => ({
    e1: 1,
    applicationTab: 0,
    review: false,
    headers: [
      { text: 'Form Name', align: 'start', filterable: false, value: 'name' },
      { text: 'Submission ID', value: 'id' },
      { text: 'Status', value: 'status' },
      { text: 'Date Submitted', value: 'submitted' }
    ],
    active: [
      { name: 'I9 Verification', id: 'I9F20201', status: 'Requires Review', submitted: 'September 8, 2022' },
      { name: 'I9 Verification', id: 'I9F20281', status: 'Requires Review', submitted: 'September 8, 2022' },
      { name: 'I9 Verification', id: 'I9F22251', status: 'Requires Review', submitted: 'September 8, 2022' },
      { name: 'I9 Verification', id: 'I9F22621', status: 'Requires Review', submitted: 'September 8, 2022' },
      { name: 'I9 Verification', id: 'I9F20221', status: 'Requires Review', submitted: 'September 8, 2022' },
      { name: 'I9 Verification', id: 'I9202521', status: 'Requires Review', submitted: 'September 8, 2022' },
      { name: 'I9 Verification', id: 'I9F52021', status: 'Requires Review', submitted: 'September 8, 2022' },
      { name: 'I9 Verification', id: 'I9F20222', status: 'Requires Review', submitted: 'September 8, 2022' }
    ]
  }),
  methods: {
    nextSection () {
      if (this.applicationTab < 1) {
        this.applicationTab = 1
      } else {
        this.$router.push('/dashboard')
      }
    }
  }
}
</script>

<style scoped>
  .contentCol {
    padding-top: 40px;
    padding-bottom: 40px;
    max-width: 1200px;
  }
  :deep(.v-data-table__wrapper:hover) {
    cursor: pointer;
  }

</style>
