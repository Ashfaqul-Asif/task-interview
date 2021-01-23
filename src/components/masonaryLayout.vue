<template>
    <div>
        <v-container>
            <Categories />
            <div class="d-flex">
                <div>

                    <v-tabs v-model="tab">
                        <v-tab dense v-for="item in items" :key="item">
                            {{ item }}
                        </v-tab>
                    </v-tabs>
                </div>
                <div class="ml-auto mr-12">
                    <v-menu nudge-bottom="50">
                        <template v-slot:activator="{ on, attrs }">
                            <v-btn v-if="$vuetify.breakpoint.mdAndDown" icon v-bind="attrs" v-on="on">
                                <v-icon>mdi-arrow-down</v-icon>
                            </v-btn>
                            <v-btn v-else text v-bind="attrs" v-on="on">
                                Recommended<v-icon>mdi-arrow-down</v-icon>
                            </v-btn>
                        </template>
                        <v-card tile max-width="300">
                            <v-list>
                                <v-list-item dense v-for="item in manuItem" :key="item" @click="() => {}">
                                    <v-list-item dense> {{ item }}</v-list-item>
                                </v-list-item>
                            </v-list>
                        </v-card>
                    </v-menu>
                </div>
            </div>


            <v-tabs-items v-model="tab">
                <v-tab-item v-for="item in items" :key="item">
                    <v-card color="basil" flat>
                        <div class="masonry">
                            <template v-for="img in images">
                                <div :key="img.id">
                                    <v-hover v-slot="{ hover }">
                                        <v-img :src="img.urls.small">
                                            <template v-slot:placeholder>
                                                <v-row class="fill-height ma-0" align="center" justify="center">
                                                    <v-progress-circular indeterminate color="#0099ff">
                                                    </v-progress-circular>
                                                </v-row>
                                            </template>
                                            <v-expand-transition>
                                                <div v-if="hover">
                                                    <v-btn class="mr-6" icon dark small absolute top right>
                                                        <v-icon>mdi-heart</v-icon>
                                                    </v-btn>
                                                    <v-btn icon dark small absolute top right>
                                                        <v-icon>mdi-plus-circle-outline</v-icon>
                                                    </v-btn>
                                                    <v-btn color="success" icon dark large absolute bottom right>
                                                        <v-icon>mdi-download-circle</v-icon>
                                                    </v-btn>
                                                    <v-btn class="ml-4" icon dark large absolute bottom left>
                                                        <v-icon>mdi-account-circle</v-icon>
                                                        <span>{{ img.user.first_name }} </span>
                                                    </v-btn>
                                                </div>
                                            </v-expand-transition>
                                        </v-img>
                                    </v-hover>
                                </div>
                            </template>
                        </div>
                    </v-card>
                </v-tab-item>
            </v-tabs-items>

        </v-container>
    </div>
</template>

<script>
    import masonaryLayout from '@/components/masonaryLayout.vue'
    import Categories from '@/components/Categories.vue'
    import axios from "axios";
    export default {
        components: {
            Categories
        },
        data() {
            return {
                images: [],
                items: [
                    'All', 'Photos', 'Freebies',
                ],
                manuItem: ['Most viewed', 'Most Download', 'Most Recent', 'Most Appreciated'],
                tab:''
            };
        },
        created() {
            axios
                .get(
                    "https://api.unsplash.com/photos?page=2&client_id=UY9J7-a3qTuJ7yf2XVF_r8naKWcvmaVdWB0GXimWR-o"
                )
                .then((res) => {
                    this.images = res.data;
                    console.log(res.data);
                });
        },
    };
</script>

<style lang="css">
    * {
        padding: 0px;
        margin: 0px;
        box-sizing: border-box;
    }

    .v-image__image {
        background-size: 100% 100%;
    }

    .masonry {
        column-count: 3;
        column-gap: 1rem;
    }

    .masonry>div {
        break-inside: avoid;
        margin-bottom: 1rem;
    }

   @media screen and (max-width: 900px) {
        .masonry {
            column-count: 2;
            column-gap: 1rem;
        }
    }

    @media screen and (max-width: 600px) {
        .masonry {
            column-count: 1;
            column-gap: 1rem;
        }
    }

    
</style>