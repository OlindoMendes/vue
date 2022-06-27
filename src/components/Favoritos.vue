<template>

    <div class="bigcontainer">
        <h3>Meus Favoritos</h3>
        <!-- <div class="container" v-for="fav in favorites" :key="fav.id">
            <h2>Title</h2>
            <p>Descrição de repo</p>
            <h5>linguagen</h5>
            <h6>updated</h6>
            <div class="btn-container">

                <button class="btn-fav"><v-icon >mdi-heart</v-icon></button>
            </div>
            
        </div> -->
        <div class="big-container" v-for="node in favorites" :key="node.id">
        
                <h2>{{ node.name }}</h2>
                <p>{{ node.description }}</p>
                <h5>{{ node.primaryLanguage }}</h5>
                <h6 id="updated">{{ node.updatedAt }}</h6>
                <div class="btn-container">

                    <button class="btn-fav" @click="addToFavourites(node.id)">
                        <v-icon>mdi-heart</v-icon>
                    </button>
                </div></div>
    </div>
</template>
<script>
import { mapState } from "vuex";
export default {
    
          computed: {
        ...mapState(['favorites']),
            haveLanguage() {
                const programLang = this.favorites.primaryLanguage ? this.favorites.primaryLanguage : 'Não identificada'
                return programLang
            }
            
    
    }
}
</script>

<style lang="scss">
.bigcontainer {
    position: relative;
    width: 1440px;
    height: 1024px;
    margin: 5em;

    /* White Background Light */

    background: #FFFFFF;

    h3 {

        font-style: normal;
        font-weight: 600;
        font-size: 21px;
        line-height: 32px;
        /* identical to box height */

        text-align: center;

        /* Primary Color */

        color: #32C0C6;
    }

    .container {
        position: absolute;
        border: 1px solid #E3E6E9;
        border-radius: 4px;
        width: 896px;
        height: 140px;
        left: 272px;
        top: 60px;

        // background-color: #32C0C6;

        .h2 {
            // position: unset;
            width: 101px;
            height: 28px;
            left: 288px;
            top: 176px;

            font-weight: 600;
            font-size: 18px;
            line-height: 28px;
            /* identical to box height, or 156% */


            /* Grey Neutral */

            color: #616161;

        }

        p {

            

            /* Paragraphy md - Poppins Regular - 14px */

           
            font-style: normal;
            font-weight: 400;
            font-size: 14px;
            line-height: 20px;
            text-align: left;
            /* or 143% */


            /* Placeholder */

            color: #8C8C8C;
        }

        h6,
        h5 {
            // position: absolute;
            display: inline-block;
            width: 97px;
            height: 18px;
            left: 288px;
            top: 266px;
        }

        .btn-container {
            /* Ellipse 2 */


            box-sizing: border-box;

            position: absolute;
            width: 40px;
            height: 40px;
            left: 840px;
            top: 15px;
            

            /* White Background Light */

            background: #FFFFFF;
            /* Primary Color */

            border: 1px solid #32C0C6;
            border-radius: 50px;


        }


    }

}
</style>