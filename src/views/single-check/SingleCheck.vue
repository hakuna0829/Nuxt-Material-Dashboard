<template>
  <v-container fluid class="down-top-padding">
    <BaseBreadcrumb
      :title="page.title"
      :icon="page.icon"
      :breadcrumbs="breadcrumbs"
    ></BaseBreadcrumb>
    <v-row>
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
      title: "Table Datatable"
    },
    breadcrumbs: [
      {
        text: "Tables",
        disabled: false,
        to: "#"
      },
      {
        text: "Table Datatable",
        disabled: true
      }
    ]
  }),
  components: {
    DatatablesSearch: () => import("./table-data/DatatablesSearch")
  }
};
</script>
