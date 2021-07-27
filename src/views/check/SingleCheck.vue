<template>
  <v-container fluid class="down-top-padding" id="verify">
    <BaseBreadcrumb
      :title="page.title"
      :icon="page.icon"
      :breadcrumbs="breadcrumbs"
    ></BaseBreadcrumb>
    <v-row>
      <v-col cols="12" md="5" lg="4">
        <v-text-field label="" placeholder="" outlined :rules="rules" dense>
          <template v-slot:append-outer>
            <div style="margin-top:-8px">
              <v-btn
                depressed
                color="#21c1d6"
                class="white--text"
                style="height:40px"
              >
                Verify
              </v-btn>
            </div>
          </template>
        </v-text-field>
      </v-col>
      <v-col cols="12" sm="12">
        <BaseCard heading="">
          <DatatablesSearch></DatatablesSearch>
        </BaseCard>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "SingleCheck",

  data: () => ({
    page: {
      title: "Single Check"
    },
    breadcrumbs: [
      {
        text: "Single Check",
        disabled: false,
        to: "/single-check"
      }
    ],
    rules: [
      value => !!value || "Required.",
      value => (value || "").length <= 20 || "Max 20 characters",
      value => {
        const pattern = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
        return (
          pattern.test(value) ||
          "Please enter a valid structure of an email address"
        );
      }
    ]
  }),
  components: {
    DatatablesSearch: () => import("./table-data/DatatablesSearch")
  }
};
</script>

<style scoped>
#verify .v-input__append-outer {
  margin-top: 0px !important;
}
</style>
