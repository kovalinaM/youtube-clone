<template>
    <div class="relative w-full">
        <input type="text" placeholder="Search" ref="input" :class="classes" :value="query" @focus="setState(true)"
            @blur="setState(false)" @click="setState(true)" @keyup.esc="handleEsc" @input="updateQuery($event.target.value)">
        <button class="absolute top-0 right-0 h-full px-3 focus:outline-none" v-show="query"  @click="updateQuery('')">
            <BaseIcon name="x" class="w-5 h-5"></BaseIcon>
        </button>
    </div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'
export default {
    inheritAttrs: false,

    components: { BaseIcon },

    props: ['query', 'hasResults'],

    emits: ['update:query', 'change-state'],

    data() {
        return {
            isActive: false,
            classes: [
                'w-full',
                'h-full',
                'px-3',
                'shadow-inner',
                'rounded-bl-sm',
                'rounded-tl-sm',
                'border',
                'border-gray-300',
                'focus:border-blue-700',
                'focus:outline-none'
            ]
        }
    },

    // computed: {
    //     searchQuery: {
    //         get() {
    //             return this.query
    //         },

    //         set(searchQuery) {
    //             this.$emit('update:query', searchQuery)
    //         }
    //     }
    // },

    methods: {
        updateQuery(query) {
            this.$emit('update:query', query)
            this.setState(this.isActive)
        },
        setState(isActive) {
            this.isActive = isActive
            this.$emit('change-state', isActive)
        },
        handleEsc() {
            this.removeSelection()
            if (this.isActive && this.hasResults) {
                this.setState(false)
            } else {
                this.$refs.input.blur()
            }
        },
        removeSelection() {
            const end = this.$refs.input.value.length
            this.$refs.input.setSelectionRange(end, end)
        }
    },

    mounted() {
        if (window.innerWidth < 640) {
            this.$el.focus();
        }
    },

}
</script>