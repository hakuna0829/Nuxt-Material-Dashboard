<template>
  <v-card class="mb-7">
    <v-card-text class="pa-5 border-top">
      <h3 class="title font-weight-regular">
        Organization Information
      </h3>
    </v-card-text>
    <v-card-text>
      <v-text-field
        v-model="firstName"
        label="Company/orgainzation name"
        filled
        background-color="transparent"
      ></v-text-field>
      <v-text-field
        v-model="lastName"
        label="Website URL"
        filled
        background-color="transparent"
      ></v-text-field>
      <v-text-field
        type="email"
        v-model="emailtext"
        label="Address"
        filled
        background-color="transparent"
      ></v-text-field>
      <v-row>
        <v-col cols="12" md="6">
          <v-text-field
            type="email"
            v-model="emailtext"
            label="City"
            filled
            background-color="transparent"
          ></v-text-field>
        </v-col>
        <v-col cols="12" md="6">
          <v-text-field
            type="email"
            v-model="emailtext"
            label="Country"
            filled
            background-color="transparent"
          ></v-text-field>
        </v-col>
      </v-row>
    </v-card-text>
    <v-card-text class="pa-5 border-top">
      <h3 class="title font-weight-regular">
        Time Zone
      </h3>
      <h4>Current time in time zone: 12:02:40</h4>
      <!-- <vue-timezone-picker
        :options="options"
        v-model="timezone"
      ></vue-timezone-picker> -->
    </v-card-text>
    <v-card-text>
      <div class="d-flex align-baseline">
        <v-btn class="text-capitalize mt-5 element-0" color="success"
          >Save</v-btn
        >&nbsp; or &nbsp;
        <a
          href="#"
          @click="$router.go(-1)"
          class="text-decoration-underline grey--text text--darken-1"
          >Go back</a
        >
      </div>
    </v-card-text>
  </v-card>
</template>

<script>
export default {
  name: "CompanyProfile",
  data: () => ({
    firstName: "Martine",
    lastName: "Knapic",
    emailtext: "knapic@gmail.com",
    password: "1234567889",
    show1: false,
    rules: {
      required: value => !!value || "Required.",
      min: v => v.length >= 8 || "Min 8 characters",
      emailMatch: () => "The email and password you entered don't match"
    },
    timezone: "America/Chicago",
    options: {
      width: 500,
      height: 250,
      defaultValue: { value: "America/Los_Angeles", attribute: "zonename" },
      quickLink: [
        {
          "America/Los Angeles": "America/Los_Angeles",
          "America/Denver": "America/Denver",
          "America/Chicago": "America/Chicago",
          "America/New York": "America/New_York"
        }
      ],
      selectClass: "Cbox",
      filterBoxClass: "Cbox",
      mapHoverType: "zonename",
      showHoverText: false
    }
  })
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
#map-container {
  max-width: 1024px;
  max-height: 768px;
  display: block;
  margin: auto;
}
.timezone-map polygon[data-selected="true"] {
  fill: #496a84;
}
.timezone-map polygon {
  fill: #bbb;
}
.timezone-map polygon.active {
  fill: #5a5a5a;
}
.timezone-map polygon:hover {
  cursor: pointer;
}
.Cbox .quickLink {
  width: 52%;
  float: right;
  padding-bottom: 11px;
  overflow-x: auto;
  white-space: nowrap;
  overflow-y: hidden;
}
.Cbox .quickLink span:hover {
  color: #fff;
  background-color: #496a84;
  cursor: pointer;
}
.Cbox select {
  width: 45%;
  float: left;
  height: 27px;
  padding: 0px 0px 0px 10px;
}
.Cbox .quickLink span.active {
  color: #fff;
  background-color: #496a84;
}
.Cbox .quickLink span {
  font-weight: 300;
  border-radius: 3px;
  color: #000;
  background-color: #fff;
  border: solid 1px #ccc;
  margin-left: 10px;
  font-size: 9px;
  padding: 4px 6px 4px 6px;
}
.filter-box .quick-link span {
  border: #999 1px solid;
}
.Cbox .country-lov {
  text-align: left;
}
</style>
