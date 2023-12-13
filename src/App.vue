<script>
import TheHeader from './components/TheHeader.vue'
import TheSidebarSmall from './components/TheSidebarSmall.vue'
import TheSidebar from './components/TheSidebar.vue'
import TheSidebarMobile from './components/TheSidebarMobile.vue'
import TheCategories from './components/TheCategories.vue'
import TheVideos from './components/TheVideos.vue'

export default {
  components: {
    TheHeader,
    TheSidebarSmall,
    TheSidebar,
    TheSidebarMobile,
    TheCategories,
    TheVideos
  },

  data() {
    return {
      isMobileSidebarOpen: false,
      sidebarState: null
    }
  },

  mounted() {
    if (window.innerWidth >= 768 && window.innerWidth < 1280) {
      this.sidebarState = 'compact'
    }

    if (window.innerWidth >= 1280) {
      this.sidebarState = 'normal'
    }

  },

  methods: {
    toggleSidebar() {
      if (window.innerWidth >= 1280) {
        this.sidebarState = this.sidebarState == 'normal' ? 'compact' : 'normal'
      } else {
        this.openMobilsSidebar()
      }
    },

    openMobileSidebar() {
      this.isMobileSidebarOpen = true
    },

    closeMobileSidebar() {
      this.isMobileSidebarOpen = false
    }
  }
}
</script>

<template>
  <TheHeader @toggle-sidebar="toggleSidebar"></TheHeader>
  <!-- Small sidebar -->
  <TheSidebarSmall></TheSidebarSmall>
  <!-- Sidebar -->
  <TheSidebar></TheSidebar>
  <!-- Mobile sidebar -->
  <TheSidebarMobile :is-open="isMobileSidebarOpen" @close="closeMobileSidebar"></TheSidebarMobile>
  <!-- Categories -->
  <TheCategories></TheCategories>
  <!-- Videos -->
  <TheVideos></TheVideos>
</template>
