<template>
    <div>
        <div class="container" v-if="search.length !== 0">
            <h3>Procure pelo nome do repositório ou de usuário</h3>
            <p>Encontre os repositórios de algum usuário no campo acima</p>
            <img src="../assets/search.svg">
        </div>
        <div v-else-if="!showSearch">
            <div class="user-container">
                <div class="user-avatar">
                    <img src="../assets/logo.png">
                    <h3>{{ user.login }}</h3>
                    <p>@mr_robot</p>
                    <h6>{{ user.bio }}</h6>
                </div>



            </div>
            <div class="big-container" v-for="node in nodes" :key="node.id">
                <h2>{{ node.name }}</h2>
                <p>{{ node.description }}</p>
                <h5>{{ node.primaryLanguage }}</h5>
                <h6 id="updated">{{ node.updatedAt }}</h6>
                <div class="btn-container">

                    <button class="btn-fav" @click="addToFavourites(node.id)">
                        <v-icon>mdi-heart</v-icon>
                    </button>
                </div>
            </div>
        </div>
    </div>
</template>
<script>
import { TRENDING_REPO_DETAILS_QUERY } from '../queries/trendingRepoDetailsQuery'
import { mapActions } from 'vuex'
// import Busca from './Busca'

const first = 10
export default {

    data() {
        return {
            search: [],
            showSearch: false,
            favourites: []
        }
    },
    apollo: {
        user: {
            query: TRENDING_REPO_DETAILS_QUERY,
            variables() {
                return {
                    login: 'OlindoMendes',
                    first,
                    queryString: 'language:' + this.searchString + ' stars:>10000',
                }
            }
        }
    },
    computed: {
        nodes() {

            return this.user.repositories.edges.map((item) => { return item.node })
        },
    },
    methods: {
        ...mapActions({ add: 'favAdded' }),
            addToFavourites(id) {
                const selectFav = this.nodes.filter((node) => {
                    return node.id === id
                })
                this.add(selectFav)


            }
    }
}
</script>


<style lang="scss">
.user-container {
    box-sizing: border-box;

    position: absolute;
    width: 448px;
    height: 420px;
    left: 24px;
    top: 104px;

    /* White Background Light */

    /* Border and Line */

    border: 1px solid #E3E6E9;
    border-radius: 4px;
    justify-content: center;

    .user-avatar {
        /* image 1 */


        position: absolute;
        width: 200px;
        height: 200px;
        left: 120px;
        top: 100px;

    }

    h3 {
        width: 151px;
        height: 32px;
        right: 20px;
        text-align: center;

        /* Heading 1 - Poppins SemiBold - 21px */

        font-family: 'Poppins';
        font-style: normal;
        font-weight: 600;
        font-size: 21px;
        line-height: 32px;
        /* identical to box height */


        /* Grey Neutral */

        color: #616161;
    }

    p {
        width: 153px;
        height: 20px;
        left: 100px;
        top: 400px;
        text-align: center;

        /* Paragraphy md - Poppins Regular - 14px */

        font-family: 'Poppins';
        font-style: normal;
        font-weight: 400;
        font-size: 14px;
        line-height: 20px;
        text-align: left;
        /* identical to box height, or 143% */

        /* Grey Dark */

        color: #4E4E4E;
    }

    h6 {
        position: absolute;
        width: 400px;
        height: 40px;
        right: 20px;
        top: 280px;

        /* Paragraphy md - Poppins Regular - 14px */

        font-family: 'Poppins';
        font-style: normal;
        font-weight: 400;
        font-size: 14px;
        line-height: 20px;
        /* or 143% */

        text-align: center;

        /* Grey Dark */

        color: #4E4E4E;
    }

}

.container {
    position: relative;
    width: 562px;
    height: 361px;
    left: 439px;
    top: 249px;
    text-align: center;

    h3 {
        position: relative;
        font-weight: bold;
        font-size: 21px;
        color: #616161;
        font-style: bold;
        top: 100px
    }

    p {
        font-style: normal;
        font-weight: 400;
        font-size: 16px;
        line-height: 24px;
        /* identical to box height */

        text-align: center;

        /* Grey Neutral */

        color: #616161;
    }

}

.big-container {
    box-sizing: border-box;

    position: relative;
    width: 896px;
    height: 140px;
    left: 520px;
    top: 80px;
    margin: 20px;

    /* White Background Light */

    background: #FFFFFF;
    /* Border and Line */

    border: 1px solid #E3E6E9;
    border-radius: 4px;

    h2 {


        // width: 101px;
        // height: 28px;
        // left: 536px;
        // top: 167px;

        /* Heading 2 - Poppins SemiBold - 18px */

        font-family: 'Poppins';
        font-style: normal;
        font-weight: 600;
        font-size: 18px;
        line-height: 28px;
        /* identical to box height, or 156% */


        /* Grey Neutral */

        color: #616161;
    }

    p {
        // width: 564px;
        // height: 40px;
        // left: 536px;
        // top: 201px;

        /* Paragraphy md - Poppins Regular - 14px */

        font-family: 'Poppins';
        font-style: normal;
        font-weight: 400;
        font-size: 14px;
        line-height: 20px;
        /* or 143% */


        /* Placeholder */

        color: #8C8C8C;
    }

    #updated,
    h5 {
        // position: absolute;
        display: inline-block;
        // width: 97px;
        // height: 18px;
        // left: 288px;
        // top: 266px;

    }

    .btn-container {
        /* Ellipse 2 */


        box-sizing: border-box;

        position: absolute;
        width: 40px;
        height: 40px;
        left: 840px;
        top: 15px;
        justify-content: center;


        /* White Background Light */

        background: #FFFFFF;
        /* Primary Color */

        border: 1px solid #32C0C6;
        border-radius: 50px;


    }
}
</style>