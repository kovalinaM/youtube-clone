<template>
    <div class="relative">
        <BaseTooltip text="Settings">
            <button @click="isOpen = !isOpen" class="relative group p-2 focus:outline-none">
                <BaseIcon name="dotsVertical"></BaseIcon>
            </button>
        </BaseTooltip>
        <transition enter-from-class="transition opacity-0 scale-95" enter-active-class="transition ease-out duration-100"
            enter-to-class="transform opacity-100 scale-100" leave-from-class="transform opacity-100 scale-100"
            leave-active-class="transition ease-in duration-75" leave-to-class="transform opacity-0 scale-95">
            <div v-show="isOpen" ref="dropdown" @keydown.esc="isOpen = false" tabindex="-1"
                :class="dropdownClasses">
                <section class="py-2 border-b">
                    <ul>
                        <DropdownSettingListItem v-for="listItem in listItems" :key="listItem.label" :icon="listItem.icon"
                            :label="listItem.label" :with-sub-menu="listItem.withSubMenu"></DropdownSettingListItem>
                    </ul>
                </section>
                <section class="py-2">
                    <ul>
                        <DropdownSettingListItem label="Restricted Mode: Off" with-sub-menu></DropdownSettingListItem>
                    </ul>
                </section>
            </div>
        </transition>
    </div>
</template>

<script>
import DropdownSettingListItem from './DropdownSettingListItem.vue'
import BaseIcon from './BaseIcon.vue'
import BaseTooltip from './BaseTooltip.vue'

export default {
    components: { DropdownSettingListItem, BaseIcon, BaseTooltip },
    data() {
        return {
            isOpen: false,
            listItems: [
                {
                    label: 'Appearance: Light',
                    icon: 'sun',
                    withSubMenu: true
                },
                {
                    label: 'Language: English',
                    icon: 'translate',
                    withSubMenu: true
                },
                {
                    label: 'Location: Russia',
                    icon: 'globeAlt',
                    withSubMenu: true
                },
                {
                    label: 'Settings',
                    icon: 'cog',
                    withSubMenu: false
                },
                {
                    label: 'Your data in YouTube',
                    icon: 'shieldCheck',
                    withSubMenu: false
                },
                {
                    label: 'questionMarkCircle',
                    icon: 'help',
                    withSubMenu: false
                },
                {
                    label: 'Keyboard shortcuts',
                    icon: 'calculator',
                    withSubMenu: false
                }
            ]
        }
    },

    computed: {
        dropdownClasses() {
            return [
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

    mounted() {
        window.addEventListener('click', event => {
            if (!this.$el.contains(event.target)) {
                this.isOpen = false
            }

        })
    },

    watch: {
        isOpen() {
            this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus())
        }
    }
}
</script>