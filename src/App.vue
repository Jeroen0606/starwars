<template>
  <v-app>
    <v-main class="application-background">
      <DashboardView/>
    </v-main>
  </v-app>
</template>

<script>
import DashboardView from "@/components/DashboardView";

export default {
  name: 'App',

  components: {
    DashboardView,
  },

  data: () => ({
    //
  }),
};
</script>

<style lang="scss">
.application-background {
  background: url("assets/starwars.jpg");
}

.text-yellow {
  color: #ffef63 !important;
}
</style>
