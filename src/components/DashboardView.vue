<template>
  <v-container>
    <v-row>
      <v-col cols="12" md="6">
        <starwars-characters></starwars-characters>
      </v-col>

      <v-col cols="12" md="6">
        <starwars-planets></starwars-planets>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
  import StarwarsCharacters from "@/components/StarwarsCharacters";
  import StarwarsPlanets from "@/components/StarwarsPlanets";
  export default {
    name: 'DashboardView',
    components: {StarwarsPlanets, StarwarsCharacters}
  }
</script>
