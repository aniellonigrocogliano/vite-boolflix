<script>
import AppSearch from "./components/AppSearch.vue";
import AppList from "./components/AppList.vue";
import AppSiderBar from "./components/AppSiderBar.vue";
export default {
  components: {
    AppSearch,
    AppList,
    AppSiderBar,
  },
};
</script>

<template>
  <AppSiderBar />
  <AppSearch />
  <AppList />

</template>

<style scoped></style>
