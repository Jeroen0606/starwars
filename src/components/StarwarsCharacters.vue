<template>
  <v-card class="character-list">
    <v-card-title class="text-yellow">Characters</v-card-title>
    <div v-if="!loading">
      <v-card  class="character-item text-yellow" v-bind:key="character.name" v-for="character in characters">
        <v-card-title>{{character.name}}</v-card-title>
        <v-card-text class="character-info text-yellow">
          Gender: {{character.gender}} <br>
          Birth Year: {{character.birth_year}}
        </v-card-text>
        <v-card-title>Starred in the following movies</v-card-title>
        <v-card-text class="text-yellow">
          <starwars-movie :movie-link="movie" v-bind:key="movie.title" v-for="movie in character.films"></starwars-movie>
        </v-card-text>
      </v-card>
    </div>
    <v-progress-circular
        indeterminate
        color="text-yellow"
        v-else
    ></v-progress-circular>
  </v-card>

</template>

<script>
import axios from 'axios';
import StarwarsMovie from "@/components/StarwarsMovie";
export default {
  name: "StarwarsCharacters",
  components: {StarwarsMovie},
  data() {
    return {
      characters: [],
      loading: true
    }
  },
  mounted() {
    axios.get('https://swapi.dev/api/people')
      .then(response => {
        this.characters = response.data.results;
        this.loading = false;
      })
      .catch(exception => {
        console.log(exception);
      })
  }
}
</script>

<style scoped lang="scss">
.character-list {
  background-color: gray !important;
  padding: 10px;
}

.character-item {
  margin-bottom: 10px;
  background-color: #383835 !important;
}
</style>
