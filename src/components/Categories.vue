<template>
    <v-sheet class="mx-auto" elevation="0">
        <v-slide-group v-model="model" :class="$vuetify.breakpoint.mdAndUp ? 'pa-4' : 'pa-0'" active-class="primary" show-arrows>
            <v-slide-item v-for="img in sliderImages" :key="img.id" v-slot="{ active, toggle }">
                <v-card  class="ma-4" height="120" width="200" @click="toggle">
                    <v-img :src="img.urls.small">
                       <v-card-title class="text-md-h5 text-sm-body-1 justify-center my-auto white--text full-height">Category</v-card-title>
                    </v-img>
                </v-card>
            </v-slide-item>
        </v-slide-group>
    </v-sheet>
</template>

<script>
    import axios from "axios";
    export default {
        data() {
            return {
                model: null,
                sliderImages: [],
                sliderImagesCategories: ['Workspace', 'Summer', 'City', 'Food', 'Portrait', 'trending', 'Sports',
                    'Workspace', 'Summer', 'City'
                ]
            }
        },
        created() {
            axios
                .get(
                    "https://api.unsplash.com/photos?page=1&client_id=UY9J7-a3qTuJ7yf2XVF_r8naKWcvmaVdWB0GXimWR-o"
                )
                .then((res) => {
                    this.sliderImages = res.data;
                    console.log(res.data, 'sliderImage');
                });
        }
    }
</script>

<style>
.full-height{
  height: 100%;
}

</style>