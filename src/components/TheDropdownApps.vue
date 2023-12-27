<template>
    <div class="relative">
        <BaseTooltip text="YouTube apps">
            <button @click="isOpen = !isOpen" class="relative group p-2 focus:outline-none">
                <BaseIcon name="viewGrid" class="w-5 h-5"></BaseIcon>
            </button>
        </BaseTooltip>
        <transition enter-from-class="transition opacity-0 scale-95" enter-active-class="transition ease-out duration-100"
            enter-to-class="transform opacity-100 scale-100" leave-from-class="transform opacity-100 scale-100"
            leave-active-class="transition ease-in duration-75" leave-to-class="transform opacity-0 scale-95">
            <div v-show="isOpen" ref="dropdown" @keydown.esc="isOpen = false" tabindex="-1" :class="dropdownClasses">
                <section class="py-2 border-b">
                    <ul>
                        <DropdownAppsListItem label="YouTube TV"></DropdownAppsListItem>
                    </ul>
                </section>
                <section class="py-2 border-b">
                    <ul>
                        <DropdownAppsListItem label="YouTube Music"></DropdownAppsListItem>
                        <DropdownAppsListItem label="YouTube Kids"></DropdownAppsListItem>
                    </ul>
                </section>
                <section class="py-2">
                    <ul>
                        <DropdownAppsListItem label="Creator Academy"></DropdownAppsListItem>
                        <DropdownAppsListItem label="YouTube for Artists"></DropdownAppsListItem>
                    </ul>
                </section>
            </div>
        </transition>
    </div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'
import DropdownAppsListItem from './DropdownAppsListItem.vue'
import BaseTooltip from './BaseTooltip.vue'

export default {
    components: { BaseIcon, DropdownAppsListItem, BaseTooltip },

    data() {
        return {
            isOpen: false
        }
    },

    mounted() {
        window.addEventListener('click', event => {
            if (!this.$el.contains(event.target)) {
                this.isOpen = false
            }

        })
    },

    computed: {
        dropdownClasses() {
            return [
                'z-10',
                'absolute',
                'top-9',
                'right-0',
                'sm:left-0',
                'bg-white',
                'w-60',
                'border',
                'border-t-0',
                'focus:outline-none'
            ]
        }
    },

    watch: {
        isOpen() {
            this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus())
        }
    }
}
</script>