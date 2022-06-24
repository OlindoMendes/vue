<template>
  <div class="hello">
    <p>Repositório - {{ repository.issues}}</p>
  </div>
</template>

<script>
import gql from 'graphql-tag'

export default {
  data(){
    return {
      repository: []
    }
  },
  apollo: {
    // Simple query that will update the 'hello' vue property
    repository: gql`query {
      repository(owner:"octocat", name:"Hello-World") {
        issues(last:20, states:CLOSED) {
          edges {
            node {
              title
              url
              labels(first:5) {
                edges {
                  node {
                     name
                  }
                }
              }
           }
          }
        }
      }
    }
`
    //query ($login: String!, $first: Int!, $after: String) {
    //         user(login: $login) {
    //         id
    //         name
    //         login
    //         avatarUrl
    //         bio
    //     repositories(first: $first, after: $after) {
    //       totalCount
    //       edges {
    //         cursor
    //         node {
    //           id
    //           name
    //           description
    //           updatedAt
    //           primaryLanguage {
    //             id
    //             name
    //           }
    //         }
    //       }
    //     }
    //   }
    // }
    // }`,
  },
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
h3 {
  margin: 40px 0 0;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
