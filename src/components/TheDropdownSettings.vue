<template>
    <div class="relative">
        <BaseTooltip text="Settings">
            <button @click="toggle" class="relative group p-2 focus:outline-none">
                <BaseIcon name="dotsVertical"></BaseIcon>
            </button>
        </BaseTooltip>
        <transition enter-from-class="transition opacity-0 scale-95" enter-active-class="transition ease-out duration-100"
            enter-to-class="transform opacity-100 scale-100" leave-from-class="transform opacity-100 scale-100"
            leave-active-class="transition ease-in duration-75" leave-to-class="transform opacity-0 scale-95">
            <div v-show="isOpen" ref="dropdown" @keydown.esc="close" tabindex="-1" :class="dropdownClasses">
                <!-- <TheDropdownSettingsMain v-if="selectedMenu === 'main'" @select-menu="showSelectedMenu"></TheDropdownSettingsMain>
                <TheDropdownSettingsAppearance v-else-if="selectedMenu === 'appearance'" @select-menu="showSelectedMenu"></TheDropdownSettingsAppearance> -->
            </div>
        </transition>
    </div>
</template>

<script>
import BaseIcon from './BaseIcon.vue'
import BaseTooltip from './BaseTooltip.vue'

export default {
    components: { BaseIcon, BaseTooltip },

    data() {
        return {
            isOpen: false,
            selectedMenu: 'main',
            dropdownClasses: [
                'z-10',
                'absolute',
                'top-9',
                '-right-full',
                'sm:right-0',
                'bg-white',
                'w-72',
                'border',
                'border-t-0',
                'focus:outline-none'
            ]
        }
    },

    // mounted() {
    //     window.addEventListener('click', event => {
    //         if (!this.$el.contains(event.target)) {
    //             // this.isOpen = false
    //             this.close()
    //         }

    //     })
    // },

    // watch: {
    //     isOpen() {
    //         this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus())
    //     }
    // },

    // methods: {
    //     showSelectedMenu(selectedMenu) {
    //         this.selectedMenu = selectedMenu;

    //         this.$refs.dropdown.focus();
    //     },

    //     close() {
    //         this.isOpen = false;

    //         setTimeout(() => this.selectedMenu = 'main', 100)
    //         this.selectedMenu = 'main';
    //     },

    //     open() {
    //         this.isOpen = true;

    //         this.selectedMenu = 'main';
    //     },

    //     toggle() {
    //         this.isOpen ? this.close() : this.open();
    //     }
    // }
}
</script>