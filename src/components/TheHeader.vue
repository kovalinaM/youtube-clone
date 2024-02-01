<template>
  <header :class="classes">
    <div :class="leftSideClasses">
      <div class="flex items-center xl:w-64 xl:bg-white pl-4">
        <button @click="$emit('toggleSidebar')" class="mr-3 sm:ml-2 sm:mr-6 focus:outline-none">
          <BaseIcon name="menu"></BaseIcon>
        </button>
        <LogoMain></LogoMain>
      </div>
    </div>
    <TheSearchWrapper v-show="isSearchShown" :is-small-screen="isSmallScreen" @close="closeMobileSearch" @open-voice-modal="isVoiceModalOpen = true" />
    <div :class="rightSideClasses">
      <BaseTooltip text="Search with your voice">
        <button class="sm:hidden p-2 focus:outline-none" @click="isVoiceModalOpen = true">
          <BaseIcon name="microphone" class="w-5 h-5"></BaseIcon>
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
  <teleport to="body">
    <BaseModal v-if="isVoiceModalOpen" @close="isVoiceModalOpen = false" />
  </teleport>
</template>

<script>
import { computed } from 'vue'
import TheDropdownApps from './TheDropdownApps.vue'
import TheDropdownSettings from './TheDropdownSettings.vue'
import LogoMain from './LogoMain.vue'
import TheSearchWrapper from './TheSearchWrapper.vue'
import ButtonLogin from './ButtonLogin.vue'
import BaseIcon from './BaseIcon.vue'
import BaseTooltip from './BaseTooltip.vue'
import BaseModal from './BaseModal.vue'

export default {
  components: { TheDropdownApps, TheDropdownSettings, BaseModal, LogoMain, TheSearchWrapper, ButtonLogin, BaseIcon, BaseTooltip },

  emits: {
    toggleSidebar: null
  },

  provide() {
    return {
      isMobileSearchActive: computed(() => this.isMobileSearchActive)
    }
  },


  data() {
    return {
      isSmallScreen: false,
      isMobileSearchActive: false,
      isVoiceModalOpen: false,
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
    isSearchShown() {
      return this.isMobileSearchShown || !this.isSmallScreen
    },

    isMobileSearchShown() {
      return this.isSmallScreen && this.isMobileSearchActive;
    },

    leftSideClasses() {
      return ['lg:w-1/4', 'flex', this.opacity]
    },

    rightSideClasses() {
      return [
        'flex',
        'items-center',
        'justify-end',
        'lg:w-1/4',
        'sm:space-x-3',
        'p-2',
        'sm:px-4',
        this.opacity
      ]
    },

    opacity() {
      return this.isMobileSearchShown ? 'opacity-0' : 'opacity-100'
    }
  },

  mounted() {
    this.onResize();
    window.addEventListener('resize', this.onResize)
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