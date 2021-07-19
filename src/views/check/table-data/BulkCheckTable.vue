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
          :headers="headers"
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
            <v-chip dark>
              {{ item.status }}
            </v-chip>
          </template>
        </v-data-table>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  name: "DatatablesSearch",

  data: () => ({
    search: "",
    headers: [
      { text: "File Name", align: "start", sortable: true, value: "name" },
      { text: "Status", value: "status", filterable: false },
      { text: "Count", value: "count", filterable: false },
      { text: "Duplicates", value: "duplicates", filterable: false },
      { text: "Action", value: "action", filterable: false },
      { text: "Verified on", value: "verified_on", filterable: false },
      { text: "Total", value: "total", filterable: false },
      { text: "Deliverable", value: "deliverable", filterable: false },
      { text: "Valid but Risky", value: "valid_but_risky", filterable: false },
      { text: "Invalid", value: "invalid", filterable: false },
      { text: "Unknown", value: "unknown", filterable: false }
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
    }
  }
};
</script>
