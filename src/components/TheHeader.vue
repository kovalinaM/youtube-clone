<template>
  <header :class="classes">
    <div :class="['lg:w-1/4', 'flex', isMobileSearchShown ? 'opacity-0' : 'opacity-100']">
      <div class="flex items-center xl:w-64 xl:bg-white pl-4">
        <button @click="$emit('toggleSidebar')" class="mr-3 sm:ml-2 sm:mr-6 focus:outline-none">
          <BaseIcon name="menu"></BaseIcon>
        </button>
        <LogoMain></LogoMain>
      </div>
    </div>
    <TheSearchMobile v-if="isMobileSearchShown" @close="closeMobileSearch"></TheSearchMobile>
    <!-- <TheSearch></TheSearch> -->
    <div  :class="['flex', 'items-center', 'justify-end', 'lg:w-1/4', 'sm:space-x-3', 'p-2', 'sm:px-4', isMobileSearchShown ? 'opacity-0' : 'opacity-100']">
      <BaseTooltip text="Search with your voice">
        <button class="sm:hidden p-2 focus:outline-none">
          <BaseIcon name="microphone" class="w-5 h-5"></BaseIcon>
        </button>
      </BaseTooltip>
      <BaseTooltip text="Search">
        <button @click.stop="isMobileSearchActive = true" class="sm:hidden p-2 focus:outline-none">
          <BaseIcon name="search" class="w-5 h-5"></BaseIcon>
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
      isMobileSearchActive: false,
      classes: [
        'flex',
        'justify-between',
        'w-full',
        'bg-white',
        'bg-opacity-95'
      ]
    }
  },

  computed: {
    isMobileSearchShown() {
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