<template>
    <section class="flex border-b border-gray-200 text-black">
        <button 
            @click.stop="$emit('back')" 
            class="p-3 focus:outline-none"
            >
            <BaseIcon name="arrowLeft"></BaseIcon>
        </button>
        <span class="p-3">{{title}}</span>
    </section>
</template>

<script>
import BaseIcon from './BaseIcon.vue'

export default {
    components: {BaseIcon},

    props: ['title'],

    emits: ['back']
}
</script>