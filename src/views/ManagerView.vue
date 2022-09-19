<template>
  <v-container class="fill-height align-start">
    <v-row justify="center">
      <v-col class="contentCol">
        <h1>Welcome, John Smith!</h1>
        <v-row class="mt-5">
          <v-col cols="12" class="col-md-6">
            <v-card elevation="0">
              <v-card-title>Form Status (Day 2)</v-card-title>
              <v-divider/>
              <v-card-text>
                <v-row>
                  <v-col>
                    123
                    Complete
                  </v-col>
                  <v-divider vertical/>
                  <v-col>
                    203
                    Incomplete
                  </v-col>
                </v-row>
              </v-card-text>
            </v-card>
          </v-col>
          <v-col cols="12" class="col-md-6">
            <v-card elevation="0">
              <v-card-title>Form Status (Day 3)</v-card-title>
              <v-divider/>
              <v-card-text>
                <v-row>
                  <v-col>
                    321
                    Complete
                  </v-col>
                  <v-divider vertical/>
                  <v-col>
                    10
                    Incomplete
                  </v-col>
                </v-row>
              </v-card-text>
            </v-card>
          </v-col>
        </v-row>
        <v-card elevation="0" class="my-10">
          <v-card-title>Notifications (1)</v-card-title>
          <v-card-subtitle>Please review the checklist below to complete any assigned tasks related to your I9 verification check.</v-card-subtitle>
          <v-card-text>
            <v-list>
              <v-list-item>
                <v-list-item-avatar>
                  <v-icon class="grey lighten-1" dark>mdi-file-document</v-icon>
                </v-list-item-avatar>

                <v-list-item-content>
                  <v-list-item-title>I9 Verification Form</v-list-item-title>
                  <v-list-item-subtitle>Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor
                    incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation
                    ullamco laboris nisi ut aliquip ex ea commodo consequat.</v-list-item-subtitle>
                </v-list-item-content>

                <v-list-item-action>
                  <v-btn rounded color="#EE2722" class="white--text px-5">View</v-btn>
                </v-list-item-action>
              </v-list-item>
            </v-list>
          </v-card-text>
        </v-card>

        <v-card elevation="0" class="my-10">
          <v-card-title>Submitted Forms</v-card-title>
          <v-card-subtitle>As we are evaluating your form, we may contact you to provide additional information. In
            this case, you will receive a notification with instructions.
          </v-card-subtitle>
          <v-card-text>
            <v-divider/>
            <v-row class="ma-2">
              <v-text-field placeholder="Search" prepend-inner-icon="mdi-magnify" outlined dense hide-details class="my-2"/>
              <v-icon class="ml-5">mdi-filter</v-icon>
              <v-spacer/>
            </v-row>
            <v-data-table :headers="headers" :items="active">
              <template v-slot:[`item.status`]="{ item }">
                <v-chip :color="item.status === 'Complete' ? 'green' : 'warning'" class="font-weight-bold white--text">
                  {{ item.status }}
                </v-chip>
              </template>
              <template v-slot:[`item.action`]="{ }">
                <v-icon>mdi-dots-horizontal</v-icon>
              </template>
            </v-data-table>
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: 'ManagerView',
  data: () => ({
    applicationTab: null,
    headers: [
      { text: 'Form Name', align: 'start', filterable: false, value: 'name' },
      { text: 'Submission ID', value: 'id' },
      { text: 'Status', value: 'status' },
      { text: 'Date Submitted', value: 'submitted' },
      { text: 'Action', value: 'action' }
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
  })
}
</script>

<style scoped>
.contentCol {
  padding-top: 40px;
  max-width: 1200px;
}

</style>
