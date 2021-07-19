<template>
  <!-- ----------------------------------------------------------------------------- -->
  <!-- DatatablesSearch -->
  <!-- ----------------------------------------------------------------------------- -->
  <div>
    <div class="mt-4">
      <v-card>
        <v-card-title>
          Bulk Email Verification History
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
          item-key="name"
          class="border"
          :custom-filter="filterOnlyCapsText"
          :footer-props="{
            'items-per-page-options': [10, 50, 200, -1]
          }"
        >
          <template v-slot:item.name="{ item }">
            {{ item.name }}
            <v-icon>mdi-cloud-download</v-icon>
          </template>
          <template v-slot:item.status="{ item }">
            <v-chip dark :color="getColor(item.status)">
              {{ item.status }}
            </v-chip>
          </template>
          <template v-slot:item.action="{ item }">
            <v-btn depressed class="custom-btn">
              <v-icon :name="item.action">mdi-play-outline</v-icon>
            </v-btn>
            <v-btn depressed class="custom-btn">
              <v-icon :name="item.action">mdi-delete-outline</v-icon>
            </v-btn>
            <v-tooltip top>
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  depressed
                  class="custom-btn"
                  v-bind="attrs"
                  v-on="on"
                  :disabled="item.status !== 'Ready to verify'"
                >
                  <v-icon :name="item.action">mdi-cards-outline</v-icon>
                </v-btn>
              </template>
              <span>Download CSV</span>
            </v-tooltip>
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
      { text: "File Name", align: "start", sortable: true, value: "name" },
      { text: "Status", value: "status", filterable: false },
      { text: "Count", value: "count", filterable: false },
      { text: "Duplicates", value: "duplicates", filterable: false },
      { text: "Action", value: "action", filterable: false },
      { text: "Verified on", value: "verified_on", filterable: false },
      { text: "Total", value: "total", filterable: false, hide: "lgAndDown" },
      {
        text: "Deliverable",
        value: "deliverable",
        filterable: false,
        hide: "lgAndDown"
      },
      {
        text: "Valid but Risky",
        value: "valid_but_risky",
        filterable: false,
        hide: "lgAndDown"
      },
      {
        text: "Invalid",
        value: "invalid",
        filterable: false,
        hide: "lgAndDown"
      },
      {
        text: "Unknown",
        value: "unknown",
        filterable: false,
        hide: "lgAndDown"
      }
    ],
    desserts: [
      {
        name: "My profile.csv",
        status: "Processing",
        count: 100,
        duplicates: 1,
        action: "",
        verified_on: "16-May-2021",
        total: "",
        deliverable: "",
        valid_but_risky: "",
        invalid: "",
        unknown: ""
      },
      {
        name: "user1.csv",
        status: "Ready to verify",
        count: 40,
        duplicates: 1,
        action: "Run",
        verified_on: "19-May-2021",
        total: 999,
        deliverable: "450 (45%)",
        valid_but_risky: "109 (11%)",
        invalid: "250 (25%)",
        unknown: "170 (17%)"
      },
      {
        name: "tester.csv",
        status: "Ready to verify",
        count: 20,
        duplicates: 2,
        action: "Run Again",
        verified_on: "16-May-2021",
        total: "",
        deliverable: "",
        valid_but_risky: "",
        invalid: "",
        unknown: ""
      },
      {
        name: "tester.csv",
        status: "Ready to verify",
        count: 20,
        duplicates: 2,
        action: "Run Again",
        verified_on: "16-May-2021",
        total: "",
        deliverable: "",
        valid_but_risky: "",
        invalid: "",
        unknown: ""
      },
      {
        name: "tester.csv",
        status: "Ready to verify",
        count: 20,
        duplicates: 2,
        action: "Run Again",
        verified_on: "16-May-2021",
        total: "",
        deliverable: "",
        valid_but_risky: "",
        invalid: "",
        unknown: ""
      },
      {
        name: "tester.csv",
        status: "Verified",
        count: 20,
        duplicates: 2,
        action: "Run Again",
        verified_on: "16-May-2021",
        total: "",
        deliverable: "",
        valid_but_risky: "",
        invalid: "",
        unknown: ""
      },
      {
        name: "tester.csv",
        status: "Running",
        count: 20,
        duplicates: 2,
        action: "Run Again",
        verified_on: "16-May-2021",
        total: "",
        deliverable: "",
        valid_but_risky: "",
        invalid: "",
        unknown: ""
      },
      {
        name: "tester.csv",
        status: "Error API",
        count: 20,
        duplicates: 2,
        action: "Run Again",
        verified_on: "16-May-2021",
        total: "",
        deliverable: "",
        valid_but_risky: "",
        invalid: "",
        unknown: ""
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
      console.log(status);
      if (status === "Uploading" || status === "Processing") return "#1e88e5";
      if (status === "Ready to verify") return "#21c1d699";
      if (status === "Verified") return "#21c1d6";
      if (status === "Running") return "#725DF4";
      if (status === "Error API") return "#ff5252";
    }
  }
};
</script>
<style scoped>
.custom-btn {
  min-width: 20px !important;
  padding: 0px 5px !important;
}
</style>
