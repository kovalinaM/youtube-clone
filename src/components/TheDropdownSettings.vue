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
                <component :is="menu" @select-menu="showSelectedMenu" @select-option="selectOption"
                    :selected-options="selectedOptions" />
            </div>
        </transition>
    </div>
</template>

<script>
import TheDropdownSettingsMain from './TheDropdownSettingsMain.vue'
import TheDropdownSettingsAppearance from './TheDropdownSettingsAppearance.vue'
import TheDropdownSettingsLanguage from './TheDropdownSettingsLanguage.vue'
import TheDropdownSettingsLocation from './TheDropdownSettingsLocation.vue'
import TheDropdownSettingsRestrictedMode from './TheDropdownSettingsRestrictedMode.vue'
import BaseIcon from './BaseIcon.vue'
import BaseTooltip from './BaseTooltip.vue'

export default {
    components: { TheDropdownSettingsMain, TheDropdownSettingsAppearance, TheDropdownSettingsLanguage, TheDropdownSettingsLocation, TheDropdownSettingsRestrictedMode, BaseIcon, BaseTooltip, TheDropdownSettingsRestrictedMode },

    data() {
        return {
            isOpen: false,
            selectedMenu: 'main',
            selectedOptions: {
                theme: {
                    id: 0,
                    text: 'Use device theme'
                },
                language: {
                    id: 0,
                    text: 'English'
                },
                location: {
                    id: 0,
                    text: 'United States'
                },          
                restrictedMode: false
                // restrictedMode: {
                //     enabled: false,
                //     text: 'Off'
                // }
            },
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

    mounted() {
        window.addEventListener('click', event => {
            if (!this.$el.contains(event.target)) {
                this.close()
            }

        })
    },

    computed: {
        menu() {
            const menuComponentNames = {
                main: 'TheDropdownSettingsMain',
                appearance: 'TheDropdownSettingsAppearance',
                language: 'TheDropdownSettingsLanguage',
                location: 'TheDropdownSettingsLocation',
                restricted_mode: 'TheDropdownSettingsRestrictedMode'
            }

            return menuComponentNames[this.selectedMenu]
        }
    },

    watch: {
        isOpen() {
            this.$nextTick(() => this.isOpen && this.$refs.dropdown.focus())
        }
    },

    methods: {
        showSelectedMenu(selectedMenu) {
            this.selectedMenu = selectedMenu;

            this.$refs.dropdown.focus();
        },

        close() {
            this.isOpen = false;

            setTimeout(() => this.selectedMenu = 'main', 100)
            this.selectedMenu = 'main';
        },

        open() {
            this.isOpen = true;

            this.selectedMenu = 'main';
        },

        toggle() {
            this.isOpen ? this.close() : this.open();
        },

        selectOption(option) {
            this.selectedOptions[option.name] = option.value
        }
    }
}
</script>