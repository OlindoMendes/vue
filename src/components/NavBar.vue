<template>
    <v-toolbar class="header">
        <v-text-field class="search" label="Buscar usuário" outlined dense><v-icon>fas fa-search</v-icon></v-text-field>

            <!-- <v-btn class="favourites" color="#32C0C6">Favoritos</v-btn> -->
        <button @click="onClick" class="button"><v-icon dark>mdi-heart-outline</v-icon> Favoritos </button> 
        

        <!-- <v-text-field placeholder="please enter the Github Repo name"></v-text-field> -->
        <!-- <v-btn>
            Favoritos
        </v-btn> -->
    </v-toolbar>
</template>
<script>
export default {
    methods: {
        onClick(){
            this.$router.push('/favourites')
        }
    }
    
}
</script>

<style lang="scss">

.header {
    position: absolute;
    width: 100%;
    height: 100%;
    left: 0px;
    top: 0px;

    .search {

        box-sizing: border-box;
        // text-decoration: none;
        position: absolute;
        width: 668px;
        height: 40px;
        left: 24px;
        top: 20px;

        /* White Background Light */

        background: #FFFFFF;
        /* Border and Line */

        border: 1px solid #E3E6E9;
        border-radius: 4px;

    }

    .button {
        position: absolute;
        width: 145px;
        height: 65px;
        left: 1295px;
        top: 0px;
        background: #32C0C6;
        color: #FFFFFF;

    }


    .favourites {
        position: absolute;
        width: 145px;
        height: 80px;
        left: 1295px;
        top: 0px;

        /* Primary Color */

        // background: #32C0C6;
    }

}
</style>