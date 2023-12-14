<script>
import TheHeader from './components/TheHeader.vue'
import TheSidebarCompact from './components/TheSidebarCompact.vue'
import TheSidebar from './components/TheSidebar.vue'
import TheSidebarMobile from './components/TheSidebarMobile.vue'
import TheCategories from './components/TheCategories.vue'
import TheVideos from './components/TheVideos.vue'

export default {
  components: {
    TheHeader,
    TheSidebarCompact,
    TheSidebar,
    TheSidebarMobile,
    TheCategories,
    TheVideos
  },

  data() {
    return {
      isMobileSidebarOpen: false,
      isCompactSidebarOpen: false,
      isSidebarOpen: false,
      isCompactSidebarActive: false
    }
  },

  mounted() {
    this.onResize()

    window.addEventListener('resize', this.onResize)

  },

  methods: {
    onResize() {
      if(window.innerWidth < 768) {
        this.isCompactSidebarOpen = false,
        this.isSidebarOpen = false
      } else if ( window.innerWidth < 1280) {
        this.isCompactSidebarOpen = true,
        this.isSidebarOpen = false
      } else {
        this.isCompactSidebarOpen = this.isCompactSidebarActive ,
        this.isSidebarOpen = !this.isCompactSidebarActive 
        this.isMobileSidebarOpen = false
      }
    },

    toggleSidebar() {
      if (window.innerWidth >= 1280) {
        this.isCompactSidebarActive = !this.isCompactSidebarActive

        this.onResize()
      } else {
        this.openMobileSidebar()
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
  <TheSidebarCompact v-if="isCompactSidebarOpen"></TheSidebarCompact>
  <!-- Sidebar -->
  <TheSidebar v-if="isSidebarOpen"></TheSidebar>
  <!-- Mobile sidebar -->
  <TheSidebarMobile :is-open="isMobileSidebarOpen" @close="closeMobileSidebar"></TheSidebarMobile>
  <!-- Categories -->
  <TheCategories :is-sidebar-open="isSidebarOpen"></TheCategories>
  <!-- Videos -->
  <TheVideos :is-sidebar-open="isSidebarOpen"></TheVideos>
</template>
