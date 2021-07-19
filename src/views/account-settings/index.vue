<template>
  <v-card>
    <v-toolbar flat>
      <template>
        <v-tabs v-model="currentItem" fixed-tabs slider-color="white">
          <v-tab
            v-for="item in items"
            :key="item.key"
            :href="'#tab-' + item.key"
          >
            {{ item.label }}
          </v-tab>
        </v-tabs>
      </template>
    </v-toolbar>

    <v-tabs-items v-model="currentItem">
      <v-tab-item
        v-for="item in items"
        :key="item.key"
        :value="'tab-' + item.key"
      >
        <v-card flat>
          <v-card-text>
            <!-- <CompanyProfile v-if="item.key === 'company'" /> -->
            <!-- {{ text }} -->
          </v-card-text>
        </v-card>
      </v-tab-item>
    </v-tabs-items>
  </v-card>
</template>

<script>
export default {
  data: () => ({
    currentItem: "tab-company",
    items: [
      { label: "Company profile", key: "company" },
      { label: "Shopping", key: "shopping" },
      { label: "Videos", key: "videos" },
      { label: "Images", key: "images" }
    ],
    text:
      "Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat."
  }),

  methods: {
    // addItem(item) {
    //   const removed = this.items.splice(0, 1);
    //   this.items.push(...this.more.splice(this.more.indexOf(item), 1));
    //   this.more.push(...removed);
    //   this.$nextTick(() => {
    //     this.currentItem = "tab-" + item;
    //   });
    // }
  },
  components: {
    // CompanyProfile: () => import("./company-profile")
  }
};
</script>
