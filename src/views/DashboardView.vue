<template>
  <v-container class="fill-height align-start">
    <v-row justify="center">
      <v-col class="contentCol">
        <h1>Welcome, John Smith!</h1>
        <v-card elevation="0" class="my-10">
          <v-card-title>Tasks (1)</v-card-title>
          <v-card-subtitle>Please review the checklist below to complete any assigned tasks related to your I9 verification check.</v-card-subtitle>
          <v-card-text>
            <v-list>
              <v-list-item>
                <v-list-item-avatar>
                  <v-icon class="grey lighten-1" dark>mdi-file-document</v-icon>
                </v-list-item-avatar>

                <v-list-item-content>
                  <v-list-item-title>I9 Verification Form</v-list-item-title>
                  <v-list-item-subtitle>Section 1</v-list-item-subtitle>
                  <P class="font-weight-bold red--text mb-0">Due: September 25, 2022</P>
                </v-list-item-content>

                <v-list-item-action>
                  <v-btn rounded color="#EE2722" class="white--text px-5" @click="$router.push('/form')">Start</v-btn>
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
            <v-tabs v-model="applicationTab" color="#EE2722">
              <v-tab>Active ({{ active.length }})</v-tab>
              <v-tab>Inactive ({{ inactive.length }})</v-tab>
            </v-tabs>
            <v-divider/>
            <v-data-table :headers="headers" :items="applicationTab ? inactive : active" disable-sort>
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
  name: 'DashboardView',
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
      {
        name: 'I9 Verification',
        id: 'I9F20221',
        status: 'Under Review',
        submitted: 'September 8, 2022'
      }
    ],
    inactive: [
      {
        name: 'I9 Verification',
        id: 'I9F20221',
        status: 'Complete',
        submitted: 'March 8, 2022'
      },
      {
        name: 'Background Check',
        id: 'BC2022312',
        status: 'Complete',
        submitted: 'January 1, 2022'
      }
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
