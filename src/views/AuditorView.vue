<template>
  <v-container class="fill-height align-start">
    <v-row justify="center">
      <v-col class="contentCol">
        <h1>Welcome, John Smith!</h1>
        <v-card elevation="0" class="my-10">
          <v-card-title>Audit Panel</v-card-title>
          <v-card-subtitle>Please review the checklist below to complete any assigned tasks related to your I9 verification check.</v-card-subtitle>
          <v-tabs v-model="applicationTab" color="#EE2722">
            <v-tab>System Activity</v-tab>
            <v-tab>Compliance</v-tab>
            <v-tab>I9 Forms</v-tab>
          </v-tabs>
          <v-divider/>
          <v-card-text>
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
  name: 'AuditorView',
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
    ],
    inactive: [
      { name: 'I9 Verification', id: 'I9F20221', status: 'Complete', submitted: 'March 8, 2022' },
      { name: 'Background Check', id: 'BC2022312', status: 'Complete', submitted: 'January 1, 2022' },
      { name: 'Background Check', id: 'BC2024312', status: 'Complete', submitted: 'January 1, 2022' },
      { name: 'Background Check', id: 'BC2026312', status: 'Complete', submitted: 'January 1, 2022' },
      { name: 'Background Check', id: 'BC2122312', status: 'Complete', submitted: 'January 1, 2022' },
      { name: 'Background Check', id: 'BC2022412', status: 'Complete', submitted: 'January 1, 2022' }
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
