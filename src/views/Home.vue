<template>
  <div class="home">
    <SearchOptions />
    <masonaryLayout/>
  </div>
</template>

<script>
// @ is an alias to /src
import SearchOptions from '@/components/SearchOptions.vue'
import masonaryLayout from '@/components/masonaryLayout.vue'

export default {
  name: 'Home',
  components: {
    SearchOptions,masonaryLayout
  }
}
</script>
