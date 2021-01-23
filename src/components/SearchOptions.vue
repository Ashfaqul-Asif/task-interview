<template>
    <div class="image">
      <v-img contain min-height='60vh' src='@/assets/coverImage.png'>
       <v-container class="full-height" >
        <v-row justify="center" align="center" class="lightbox white--text pa-2 fill-height">
          <v-col  cols='12' md='8' sm='10'> 
            <div class="text-md-h4 text-sm-h6 ">Your local source of high quality images and videos directly from their creators</div>
             <v-text-field class="mt-4" rounded solo label="Search photos and videos" append-icon="mdi-magnify"
             ></v-text-field>
             <span class="pl-4"> <strong>Recommended:</strong> summer, food, covid-19, real estate, love</span>
          </v-col>
        </v-row>
       </v-container>
      </v-img>
    </div>
</template>

<script>
  export default {
    name: 'SearchOptions',
    data: () => ({
     
    
    }),
  }
</script>

<style lang='scss'>
 .image{
   position: relative;
   &__context{
     position: absolute;

   }
 }
.v-image__image{
 background-size:100% 100%;
}
.full-height{
  height: 100%;
}

</style>

