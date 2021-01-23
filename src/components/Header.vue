<template>
    <div>
        <v-app-bar depressed>
            <div v-if="$vuetify.breakpoint.mdAndDown">
                <v-app-bar-nav-icon @click="drawer = true"></v-app-bar-nav-icon>
            </div>
            <v-toolbar-title class="orange--text">CLICK MOTTO</v-toolbar-title>
            <v-spacer></v-spacer>
            <div v-if="$vuetify.breakpoint.mdAndUp">
                <v-btn class="text-none" plain small text>Explore</v-btn>
                <v-btn class="text-none" plain small text>Discover</v-btn>
                <v-btn class=" text-none" plain small text>For Professionals</v-btn>
                <v-menu content-class="my-menu" nudge-bottom="50">

                    <template v-slot:activator="{ on, attrs }">
                        <v-btn icon v-bind="attrs" v-on="on">
                            <v-icon>mdi-dots-horizontal</v-icon>
                        </v-btn>
                    </template>
                    <v-card tile  max-width="300">
                        <v-list>
                            <v-list-item dense v-for="item in manuItem" :key="item" @click="() => {}">
                                <v-list-item dense> {{ item }}</v-list-item>
                            </v-list-item>
                        </v-list>
                        <v-divider></v-divider>
                        <v-list class="d-flex">
                            <v-list-item class="" v-for='icon in menuIcon' :key="icon">
                                <v-icon>{{icon}}</v-icon>
                            </v-list-item>
                        </v-list>

                    </v-card>
                </v-menu>
                
                <v-btn class="text-none" rounded-lg small outlined>submit photos</v-btn>
                <v-divider style="border: 1px solid #B9B9B9" inset class="ml-4" vertical></v-divider>
                <v-btn class=" text-none" plain small text>Login</v-btn>
                <v-btn class="text-none" small depressed color="error">
                    Join Free
                </v-btn>
            </div>


        </v-app-bar>
        <v-navigation-drawer v-model="drawer" absolute temporary>
                    <v-list nav dense>
                        <v-list-item-group v-model="group" active-class="deep-purple--text text--accent-4">
                            <v-list-item  v-for="(item,index) in navItem" :key="index">
                                <v-list-item-title class="ml-4">{{item}}</v-list-item-title>
                            </v-list-item>
                            
                        </v-list-item-group>
                    </v-list>
            </v-navigation-drawer>
    </div>
</template>

<script>
    export default {
        data() {
            return {
                manuItem: ['About Click Motto', 'Pricing', 'License', 'Partnership', 'Blog', 'Help', 'Join The Team'],
                menuIcon: ['mdi-facebook', 'mdi-twitter', 'mdi-instagram', 'mdi-pinterest'],
                drawer: false,
                group: null,
                navItem:['Explore','Discover','For Professional','submit photo','Login','Join Free']
            }
        },
    };
</script>

<style>
   
</style>