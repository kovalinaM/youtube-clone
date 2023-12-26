<template>
    <div class="relative">
        <img
            src="https://i.ytimg.com/vi/ANj7qUgzNq4/hqdefault.jpg?sqp=-oaymwEbCKgBEF5IVfKriqkDDggBFQAAiEIYAXABwAEG&rs=AOn4CLCEC_xrlasDyU31TouJxFudHUrsPQ">
        <VideoItemThumbnailButton icon="clock" label="Watch later" class="top-0"/>
        <VideoItemThumbnailButton icon="menuAlt" label="Add to queue" class="top-8"/>
    <span
        class="opacity-100 group-hover:opacity-0 duration-500 absolute bottom-0 right-0 bg-black text-white rounded-sm m-1 p-1 text-xs font-semibold">6:35</span>
</div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'
import VideoItemThumbnailButton from './VideoItemThumbnailButton.vue'

export default {
    components: {BaseIcon, VideoItemThumbnailButton}
}
</script>

