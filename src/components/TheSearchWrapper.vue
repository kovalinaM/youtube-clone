<template>
    <div
      :class="classes">
      <BaseTooltip v-if="isSmallScreen" text="Back" right>
        <button @click="$emit('close')" class="mr-2 p-2 focus:outline-none p-2">
          <BaseIcon name="arrowLeft" class="w-5 h-5"></BaseIcon>
        </button>
      </BaseTooltip>
      <TheSearch/>
      <BaseTooltip text="Search with your voice" :left="isSmallScreen">
        <button @click="$emit('open-voice-modal')" class="p-2 focus:outline-none p-2">
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

    props: ['isSmallScreen'],

    emits: ['close', 'open-voice-modal'],

    computed: {
      classes() {
        return this.isSmallScreen
          ? ['absolute', 'w-full', 'p-2', 'z-10', 'flex']
          : [
              'hidden',
              'sm:flex',
              'items-center',
              'justify-end',
              'p-2.5','pl-8',
              'md:pl-12',
              'md:px-8',
              'flex-1',
              'lg:px-0',
              'lg:w-1/2',
              'max-w-screen-md'
            ]
      }
    },

    mounted() {
      window.addEventListener('click', this.onClick)
    },

    methods: {
      onClick(event) {
        if(!this.$el.contains(event.target)) {
          this.$emit('close')
        }
      }
    }
}
</script>