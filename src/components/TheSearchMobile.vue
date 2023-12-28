<template>
    <div class="absolute w-full p-2 z-10 flex">
        <BaseTooltip text="Back" right>
            <button @click="$emit('close')" class="mr-2 p-2 focus:outline-none p-2">
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
    components: { TheSearch, BaseTooltip, BaseIcon },

    mounted() {
        window.addEventListener('click', this.onClick)
    },

    beforeUnmount() {
        window.removeEventListener('click', this.onClick)
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