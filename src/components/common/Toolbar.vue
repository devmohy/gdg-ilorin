<template>
  <v-toolbar
    app
    color="white"
    height="55px"
    scroll-off-screen
  >
  
    <v-toolbar-side-icon
      class="hidden-md-and-up"
      @click="toggleDrawer"

    />

    <v-toolbar-title class="ml-0 pl-1 mr-1">
      <span class="google-font">{{ChapterDetails.ChapterName}}</span>
    </v-toolbar-title>
    <v-spacer />
    <v-btn
        v-for="(link, i) in links"
        :key="i"
        :to="link.to"
        class="ml-0 google-font hidden-sm-and-down"
        style="text-transform: capitalize;" 
        flat
        @click="onClick($event, link)"
      >
        {{ link.text }}
    </v-btn>

  
  </v-toolbar>
</template>

<style scoped>
  .google-line {
    height: 3px;
    width: 100%;
    position: relative;
    z-index: 2;
    background-image: linear-gradient(to right, #f76570 0%, #f76570 8%, #f3a46b 8%, #f3a46b 16%, #f3a46b 16%, #ffd205 16%, #ffd205 24%, #ffd205 24%, #1bbc9b 24%, #1bbc9b 25%, #1bbc9b 32%, #14b9d5 32%, #14b9d5 40%, #c377e4 40%, #c377e4 48%, #f76570 48%, #f76570 56%, #f3a46b 56%, #f3a46b 64%, #ffd205 64%, #ffd205 72%, #1bbc9b 72%, #1bbc9b 80%, #14b9d5 80%, #14b9d5 80%, #14b9d5 89%, #c377e4 89%, #c377e4 100%);
  }
</style>


<script>
import ChapterDetails from '@/assets/data/chapterDetails.json'
  // Utilities
  import {
    mapGetters,
    mapMutations
  } from 'vuex'
  export default {
    data() {
      return {
        ChapterDetails:ChapterDetails
      }
    },
    computed: {
      ...mapGetters(['links'])
    },
    methods: {
      ...mapMutations(['toggleDrawer']),
      onClick (e, item) {
        e.stopPropagation()
        if (item.to || !item.href) return
        this.$vuetify.goTo(item.href)
      }
    }
  }
</script>