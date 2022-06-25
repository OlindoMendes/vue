<template>
    <v-toolbar dark color="primary">
        <v-toolbar-title class="white--text">

            <!-- <v-icon medium></v-icon> -->
            <nav>
                <router-link to="/">GitHub Graphql</router-link> |
            </nav>
        </v-toolbar-title>
        <!-- <v-input>kuhkhhknkn</v-input> -->

        <v-text-field placeholder="please enter the Github Repo name"></v-text-field>

        <v-btn  style="height:63px; background-color:aqua ">
            Favoritos
        </v-btn>
    </v-toolbar>
</template>

<style lang="scss">
router-link {
    padding: 30px;

    a {
        font-weight: bold;
        color: #2c3e50;

        &.router-link-exact-active {
            color: #42b983;
        }
    }
}
</style>