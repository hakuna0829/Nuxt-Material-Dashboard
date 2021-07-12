<template>
  <v-row>
    <v-col cols="12" md="6" class="py-0">
      <v-card class="mb-7">
        <v-card-text class="pa-5">
          <h2 class="font-weight-regular">{{ prg1[0] }}</h2>
          <h6
            class="body-2 mb-1 blue-grey--text text--lighten-2 font-weight-light"
          >
            Total Credits Available
          </h6>
          <v-progress-linear
            rounded
            v-model="prg1[1]"
            color="success"
            class="mt-2"
          ></v-progress-linear>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col cols="12" md="6" class="py-0">
      <v-card class="mb-7">
        <v-card-text class="pa-5">
          <h2 class="font-weight-regular">{{prg3[0]}}%</h2>
          <h6
            class="body-2 mb-1 blue-grey--text text--lighten-2 font-weight-light"
          >
            Product A
          </h6>
          <v-progress-linear
            rounded
            v-model="prg3[1]"
            color="error"
            class="mt-2"
          ></v-progress-linear>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col cols="12" md="6" class="py-0">
      <v-card class="mb-7">
        <v-card-text class="pa-5">
          <h2 class="font-weight-regular">40%</h2>
          <h6
            class="body-2 mb-1 blue-grey--text text--lighten-2 font-weight-light"
          >
            Pending Product
          </h6>
          <v-progress-linear
            rounded
            v-model="prg2"
            color="info"
            class="mt-2"
          ></v-progress-linear>
        </v-card-text>
      </v-card>
    </v-col>
    <v-col cols="12" md="6" class="py-0">
      <v-card class="mb-7">
        <v-card-text class="pa-5">
          <h2 class="font-weight-regular">28%</h2>
          <h6
            class="body-2 mb-1 blue-grey--text text--lighten-2 font-weight-light"
          >
            Product B
          </h6>
          <v-progress-linear
            rounded
            v-model="prg4"
            color="black"
            class="mt-2"
          ></v-progress-linear>
        </v-card-text>
      </v-card>
    </v-col>
  </v-row>
</template>

<script>
export default {
  name: "TheProgressCard",
  data: () => ({
    prg1: ["34,987", 86],
    prg2: ["2 / 5", 56],
    prg3: ["345", 40],
    prg4: ["30011", 28]
  })
};
</script>
