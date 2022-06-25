<template>
  <v-container grid-list-md text-xs-center>
    <div v-if="$apollo.loading">
      <v-progress-circular
      :size="70"
      :width="7"
      color="primary"
      indeterminate
    ></v-progress-circular>
    </div>
    <v-layout row wrap v-else>
      <v-flex v-for="dev in user" :key="dev.id" xs3>  
      <h2>{{dev.repositories}}</h2>        
        <v-card class="cardHeight">
          <v-card-title class="cardColor white--text justify-center">
            <!-- <h2>{{dev.name}}</h2> -->
          </v-card-title>
          <v-avatar
          :size="100"
          color="grey lighten-4"
        >
          <img  :src="dev.avatarUrl" alt="avatar">
        </v-avatar>
          <v-card-actions class="justify-center">
          <h3>{{user.repositories.totalCount}}</h3>
          <a  target="_blank">
            <v-btn text color="primary">View</v-btn>
          </a>
          <h3> fav </h3>
        </v-card-actions>
        </v-card>
        <v-spacer></v-spacer>
      </v-flex>
    </v-layout>
  </v-container>
</template>

<script>
import { TRENDING_REPO_DETAILS_QUERY } from '../queries/trendingRepoDetailsQuery'

const first = 10
export default {
  props: ['searchString'],
  data () {
    return {
      search: [],
      queryString: '',
    }
  },
  apollo: {
    user: {
      query: TRENDING_REPO_DETAILS_QUERY,
      variables () {
        return {
          login:'OlindoMendes',
          first,
          queryString: 'language:' + this.searchString + ' stars:>10000',
        }
      }
    }
  }
}
</script>

<style>
.cardHeight {
  height: 200px;
  padding: 10px;
  margin: 2px;
}
</style>