<template>
  <!-- ----------------------------------------------------------------------------- -->
  <!-- DatatablesSearch -->
  <!-- ----------------------------------------------------------------------------- -->
  <div>
    <div class="mt-4">
      <v-card>
        <v-card-title>
          Single Email Verification History
          <v-spacer></v-spacer>
          <v-text-field
            v-model="search"
            append-icon="mdi-magnify"
            label="Search"
            single-line
            hide-details
          ></v-text-field>
        </v-card-title>
        <v-data-table
          :headers="computedHeaders"
          :items="desserts"
          :search="search"
          item-key="email"
          class="border"
          :custom-filter="filterOnlyCapsText"
          :footer-props="{
            'items-per-page-options': [10, 50, 200, -1]
          }"
        >
          <template v-slot:item.email="{ item }">
            <p class="email">{{ item.email }}</p>
          </template>
          <template v-slot:item.status="{ item }">
            <v-tooltip right>
              <template v-slot:activator="{ on, attrs }">
                <v-chip
                  dark
                  :color="getColor(item.status)"
                  v-bind="attrs"
                  v-on="on"
                >
                  {{ item.status }}
                </v-chip>
              </template>
              <span style="width:50%">{{ getTooltip(item.status) }}</span>
            </v-tooltip>
          </template>
          <template v-slot:item.domain="{ item }">
            <p class="email">{{ item.domain }}</p>
          </template>
        </v-data-table>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  name: "DatatablesSearch",
  computed: {
    computedHeaders() {
      return this.headers.filter(
        h => !h.hide || !this.$vuetify.breakpoint[h.hide]
      );
    }
  },
  data: () => ({
    search: "",
    headers: [
      { text: "Email", align: "start", sortable: true, value: "email" },
      { text: "Status", value: "status", filterable: false },
      { text: "Reason", value: "reason", filterable: false },
      { text: "Domain", value: "domain", filterable: false },
      {
        text: "Accept all",
        value: "accepted",
        filterable: false
      },
      { text: "Disposable", value: "disposable", filterable: false },
      { text: "Free", value: "free", filterable: false },
      { text: "Role", value: "role", filterable: false },
      {
        text: "Disabled",
        value: "disabled",
        filterable: false
      },
      { text: "Provider", value: "provider", filterable: false },
      {
        text: "Verified on",
        value: "verified_on",
        filterable: false
      },
      {
        text: "Verified by",
        value: "verified_by",
        filterable: false
      }
    ],
    desserts: [
      {
        email: "knapicm@gmail.com",
        status: "Deliverable",
        reason: "Accepted",
        domain: "gmail.com",
        accepted: "Yes",
        disposable: "No",
        free: "Yes",
        role: "No",
        disabled: "unknown",
        provider: "Outlook.com",
        verified_on: "15-Jun-2021",
        verified_by: "Martin Knapic"
      },
      {
        email: "user1@gmail.com",
        status: "Valid but Risky",
        reason: "Deliverability",
        domain: "gmail.com",
        accepted: "No",
        disposable: "No",
        free: "Yes",
        role: "No",
        disabled: "no",
        provider: "Outlook.com",
        verified_on: "18-Jun-2021",
        verified_by: "user1"
      },
      {
        email: "tester2@gmail.com",
        status: "Deliverable",
        reason: "Accepted",
        domain: "gmail.com",
        accepted: "Yes",
        disposable: "No",
        free: "Yes",
        role: "No",
        disabled: "unknown",
        provider: "Outlook.com",
        verified_on: "5-Jul-2021",
        verified_by: "William John"
      },
      {
        email: "someone.surnamexyz@bestemailverifier.com",
        status: "Unknown",
        reason: "Accepted",
        domain: "bestemailverifier.com",
        accepted: "Yes",
        disposable: "No",
        free: "Yes",
        role: "No",
        disabled: "unknown",
        provider: "Outlook.com",
        verified_on: "5-Jul-2021",
        verified_by: "William John"
      },
      {
        email: "someone.surnamexyz@bestemailveri2fier.com",
        status: "Invalid",
        reason: "Accepted",
        domain: "bestemailverifier.com",
        accepted: "Yes",
        disposable: "No",
        free: "Yes",
        role: "No",
        disabled: "unknown",
        provider: "Outlook.com",
        verified_on: "5-Jul-2021",
        verified_by: "William John"
      }
    ]
  }),
  methods: {
    filterOnlyCapsText(value, search, item) {
      console.log("value, search, item", value, search, item);
      return (
        value != null &&
        search != null &&
        typeof value === "string" &&
        value
          .toString()
          .toLocaleLowerCase()
          .indexOf(search) !== -1
      );
    },
    getColor(status) {
      if (status === "Deliverable") return "#26c6da";
      if (status === "Valid but Risky") return "#745af2";
      if (status === "Invalid") return "#f62d51";
      if (status === "Unknown") return "#dadada";
      // if (status === "Running") return "#ff5252";
    },
    getTooltip(status) {
      if (status === "Deliverable")
        return "For deliverable emails there is a 98% chance that your email will reach the owner's inbox. We recommend you use only deliverable addresses for email outreach campaigns.";
      if (status === "Valid but Risky")
        return "Valid emails indicate that email might be deliverable but no system can guarantee its existence because the emails server is set to “accept all” emails. Validity is confirmed for example by checking the syntax of the email and responsiveness of the email server of the domain used.";
      if (status === "Invalid")
        return "Invalid emails will likely not reach the destination. ";
      if (status === "Unknown")
        return "We weren’t able to verify the deliverability of the email address. Most likely because the server has not responded to our requests. We do not charge for unknown checks. ";
    }
  }
};
</script>

<style lang="scss" scoped>
#verify .v-input__append-outer {
  margin-top: 0px !important;
}

.email {
  margin: 0px;
  max-width: 100px;
  overflow: hidden;
  white-space: nowrap;
  text-overflow: ellipsis;
  @media (min-width: 1904px) {
    max-width: 180px;
    margin: 0px;
  }
}
</style>
