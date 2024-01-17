<template>
    <div
      class="fixed bg-white w-full h-14 p-3 z-10 flex">
      <BaseTooltip @click="$emit('close')" text="Back" right>
        <button class="mr-2 p-2 focus:outline-none p-2">
          <BaseIcon name="arrowLeft" class="w-5 h-5"></BaseIcon>
        </button>
      </BaseTooltip>
      <TheSearch></TheSearch>
      <BaseTooltip text="Search with your voice" left>
        <button class="p-2 focus:outline-none p-2">
          <BaseIcon name="microphone" class="w-5 h-5"></BaseIcon>
        </button>
      </BaseTooltip>
    </div>
</template>

<script>
import TheSearch from './TheSearch.vue'
import BaseTooltip from './BaseTooltip.vue'
import BaseIcon from './BaseIcon.vue'

export default {
    components: {TheSearch, BaseTooltip, BaseIcon},

    mounted() {
      window.addEventListener('click', this.onClick)
    },

    beforeUnmounted() {
      window.removeEventListener('click', this.onClick)
    },

    methods: {
      onClick(event) {
        if(!this.$el.contains(event.tsrget)) {
          this.$emit('close')
        }
      }
    }
}
</script>