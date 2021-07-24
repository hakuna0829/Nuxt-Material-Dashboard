<template>
  <v-container fluid class="down-top-padding" id="verify">
    <BaseBreadcrumb
      :title="page.title"
      :icon="page.icon"
      :breadcrumbs="breadcrumbs"
    ></BaseBreadcrumb>
    <v-row>
      <v-col cols="12" sm="12">
        <BaseCard>
          <BasicInformation></BasicInformation>
        </BaseCard>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
export default {
  name: "Profile",

  data: () => ({
    page: {
      title: "Add New User"
    },
    breadcrumbs: [
      {
        text: "Add New User",
        disabled: false,
        to: "/new-user"
      }
    ],
    name: "Martin",
    avatar: "https://ca.slack-edge.com/TGUK83BPA-U01KTG7MK34-g19920895070-512",
    filelist: [] // Store our uploaded files
  }),
  methods: {
    onButtonClick() {
      this.$refs.file.click();
    }
  },
  components: {
    BasicInformation: () => import("./BasicInformation")
    // DialogsForm: () => import("./DialogsForm")
  }
};
</script>
<style scoped lang="scss">
.avatar {
  margin-right: 10px;
}
.v-btn {
  max-width: 150px;
}
</style>
