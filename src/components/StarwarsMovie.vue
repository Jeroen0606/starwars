<template>
  <div>{{movie?.title}} - ({{movie?.release_date}})</div>
</template>

<script>
import axios from "axios";

export default {
  name: "StarwarsMovie",
  props: {
    movieLink: String
  },
  data() {
    return {
      movie: null
    }
  },
  mounted() {
    axios.get(this.movieLink)
      .then(response => {
        this.movie = response.data;
      })
      .catch(exception => {
        console.log(exception);
      })
  }
}
</script>

<style scoped>

</style>
