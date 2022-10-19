<template>
  <v-card class="planets-list text-yellow">
    <v-card-title class="text-yellow">Planets</v-card-title>
    <v-card-text>
      <v-text-field
          prepend-inner-icon="mdi-magnify"
          v-model="query"
          color="#ffef63">
      </v-text-field>
      <div v-if="!loading">
        <v-card v-bind:key="planet.name" v-for="planet in planets">
          <v-card-text class="planet-item text-yellow">{{planet.name}}</v-card-text>
        </v-card>
      </div>
      <v-progress-circular
          indeterminate
          color="text-yellow"
          v-else
      ></v-progress-circular>
    </v-card-text>
  </v-card>
</template>

<script>
import axios from "axios";
export default {
  name: "StarwarsPlanets",
  data() {
    return {
      query: "",
      planets: [],
      loading: true
    }
  },
  methods: {
    getPlanets() {
      this.loading = true;

      let queryString = '';
      if (this.query !== '') {
        queryString = '/?search=' + this.query;
      }

      axios.get('https://swapi.dev/api/planets' + queryString)
        .then(response => {
          this.planets = response.data.results;
          this.loading = false;
        })
        .catch(exception => {
          console.log(exception);
        })
    }
  },
  watch: {
    query() {
      this.getPlanets();
    }
  },
  mounted() {
    this.getPlanets();
  }
}
</script>

<style lang="scss">
.planets-list {
  background-color: gray !important;
  padding: 10px;
}

.planet-item {
  margin-bottom: 10px;
  background-color: #383835 !important;
}
</style>
