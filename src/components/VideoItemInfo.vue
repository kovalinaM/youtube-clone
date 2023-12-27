<template>
    <div class="flex items-start mt-3">
        <img src="https://i.ytimg.com/vi/TiBCLraUFvA/hqdefault.jpg?sqp=-oaymwEbCKgBEF5IVfKriqkDDggBFQAAiEIYAXABwAEG&rs=AOn4CLASU2Kfpcm7HQhJdpWDf9uX5GKbGg"
            class="mr-3 rounded-full w-9 h-9" alt="">
        <div class="text-sm">
            <span class="font-semibold text-gray-800">Video title {{ index }}</span>
            <div class="mt-1 flex">
                <BaseTooltip text="channelName" top>
                    <span>{{ channelName }}</span>
                </BaseTooltip>
                <BaseTooltip text="Verified" top>
                    <BaseIcon name="checkCircle" class="w-3.5 h-3.5 ml-1"></BaseIcon>
                </BaseTooltip>
            </div>
            <div v-html="summary">
            </div>
        </div>
        <VideoItemDropdown></VideoItemDropdown>
    </div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'
import VideoItemDropdown from './VideoItemDropdown.vue'
import BaseTooltip from './BaseTooltip.vue'

export default {
    components: { BaseIcon, VideoItemDropdown, BaseTooltip },
    props: ['index'],

    data() {
        return {
            channelName: `Channel name ${this.index}`
        }
    },

    computed: {
        summary() {
            const days = this.index === 1 ? 'day' : 'days'

            return `${this.index}K views &middot; ${this.index} ${days} ago`
        }
    }
}
</script>