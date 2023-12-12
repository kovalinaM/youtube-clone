<template>
    <div class="relative">
        <img
            src="https://i.ytimg.com/vi/ANj7qUgzNq4/hqdefault.jpg?sqp=-oaymwEbCKgBEF5IVfKriqkDDggBFQAAiEIYAXABwAEG&rs=AOn4CLCEC_xrlasDyU31TouJxFudHUrsPQ">
        <span
            class="opacity-0 group-hover:opacity-100 bg-opacity-60 absolute top-0 right-0 bg-black text-white rounded-sm m-1 p-1">
            <BaseIcon  name="clock" class="w-5 h-5"></BaseIcon>
        </span>
        <span
        class="opacity-0 group-hover:opacity-100 bg-opacity-60 absolute top-8 right-0 bg-black text-white rounded-sm m-1 p-1">
        <BaseIcon  name="menuAlt" class="w-5 h-5"></BaseIcon>
    </span>
    <span
        class="opacity-100 group-hover:opacity-0 duration-500 absolute bottom-0 right-0 bg-black text-white rounded-sm m-1 p-1 text-xs font-semibold">6:35</span>
</div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'

export default {
    components: {BaseIcon}
}
</script>

