<template>
  <header class="flex justify-between fixed z-30 w-full">
    <div class="lg:w-1/4 flex">
      <div class="flex items-center xl:w-64 xl:bg-white pl-4">
        <button @click="$emit('toggleSidebar')" class="mr-3 sm:ml-2 sm:mr-6 focus:outline-none">
          <BaseIcon name="menu"></BaseIcon>
        </button>
        <LogoMain></LogoMain>
      </div>
    </div>
    <TheSearchMobile 
      v-if="isMobileSearchShow"
      @close="closeMobileSearch"
    ></TheSearchMobile>
    <div v-else class="flex items-center justify-end lg:w-1/4 sm:space-x-3 p-2 sm:px-4">
      <BaseTooltip text="Search with your voice">
        <button class="sm:hidden p-2 focus:outline-none">
          <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd"
              d="M7 4a3 3 0 016 0v4a3 3 0 11-6 0V4zm4 10.93A7.001 7.001 0 0017 8a1 1 0 10-2 0A5 5 0 015 8a1 1 0 00-2 0 7.001 7.001 0 006 6.93V17H6a1 1 0 100 2h8a1 1 0 100-2h-3v-2.07z"
              clip-rule="evenodd"></path>
          </svg>
        </button>
      </BaseTooltip>
      <BaseTooltip text="Search">
        <button @click.stop="isMobileSearchActive = true" class="sm:hidden p-2 focus:outline-none">
          <svg class="w-5 h-5" fill="currentColor" viewBox="0 0 20 20" xmlns="http://www.w3.org/2000/svg">
            <path fill-rule="evenodd"
              d="M8 4a4 4 0 100 8 4 4 0 000-8zM2 8a6 6 0 1110.89 3.476l4.817 4.817a1 1 0 01-1.414 1.414l-4.816-4.816A6 6 0 012 8z"
              clip-rule="evenodd"></path>
          </svg>
        </button>
      </BaseTooltip>
      <TheDropdownApps></TheDropdownApps>
      <TheDropdownSettings></TheDropdownSettings>
      <ButtonLogin></ButtonLogin>
    </div>
  </header>
</template>

<script>
import TheDropdownApps from './TheDropdownApps.vue'
import TheDropdownSettings from './TheDropdownSettings.vue'
import LogoMain from './LogoMain.vue'
import TheSearch from './TheSearch.vue'
import ButtonLogin from './ButtonLogin.vue'
import BaseIcon from './BaseIcon.vue'
import BaseTooltip from './BaseTooltip.vue'
import TheSearchMobile from './TheSearchMobile.vue'

export default {
  components: { TheDropdownApps, TheDropdownSettings, LogoMain, TheSearch, ButtonLogin, BaseIcon, BaseTooltip, TheSearchMobile },

  emits: {
    toggleSidebar: null
  },

  data() {
    return {
      isSmallScreen: false,
      isMobileSearchActive: false
    }
  },

  computed: {
    isMobileSearchShow() {
      return this.isSmallScreen && this.isMobileSearchActive;
    }
  },

  mounted() {
    this.onResize();
    window.addEventListener('resize', this.onResize);
  },

  methods: {
    onResize() {
      if (window.innerWidth < 640) {
        this.isSmallScreen = true;
        return
      } 

      this.closeMobileSearch();
      this.isSmallScreen = false;
    },

    closeMobileSearch() {
      this.isMobileSearchActive = false
    }
  }
}
</script>