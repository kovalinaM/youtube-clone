<template>
    <section class="py-2 border-b">
        <ul>
            <DropdownSettingListItem 
                v-for="listItem in listItems.slice(0, 8)" 
                :key="listItem.label"
                :label="listItem.label" 
                :icon="listItem.icon" 
                :with-sub-menu="listItem.withSubMenu"
                @click.stop="selectMenu(listItem)" />
        </ul>
    </section>
    <section class="py-2">
        <ul>
            <DropdownSettingListItem 
                :label="listItems[8].label" 
                :icon="listItems[8].icon" 
                :with-sub-menu="listItems[8].withSubMenu" 
                @click.stop="selectMenu(listItems[8])"/>
        </ul>
    </section>
</template>

<script>
import DropdownSettingListItem from './DropdownSettingListItem.vue'

export default {
    components: { DropdownSettingListItem },

    props: ['selectedOptions'],

    emits: ['select-menu', 'select-option'],

    data() {
        return {
            listItems: [
                {
                    id: 'appearance',
                    label: 'Appearance: ' + this.selectedOptions.theme.text,
                    icon: 'sun',
                    withSubMenu: true
                },
                {
                    id: 'language',
                    label: 'Language: ' + this.selectedOptions.language.text,
                    icon: 'translate',
                    withSubMenu: true
                },
                {
                    id: 'location',
                    label: 'Location: ' + this.selectedOptions.location.text,
                    icon: 'globeAlt',
                    withSubMenu: true
                },
                {
                    id: 'settings',
                    label: 'Settings',
                    icon: 'cog',
                    withSubMenu: false
                },
                {
                    id: 'your_data_in_youtube',
                    label: 'Your data in YouTube',
                    icon: 'shieldCheck',
                    withSubMenu: false
                },
                {
                    id: 'help',
                    label: 'Help',
                    icon: 'questionMarkCircle',
                    withSubMenu: false
                },
                {
                    id: 'feedback',
                    label: 'Send feedback',
                    icon: 'chatAlt',
                    withSubMenu: false
                },
                {
                    id: 'keyboard_shortcuts',
                    label: 'Keyboard shortcuts',
                    icon: 'calculator',
                    withSubMenu: false
                },
                {
                    id: 'restricted_mode',
                    label: 'Restricted Mode: ' + this.selectedOptions.restrictedMode.text,
                    icon:  null,
                    withSubMenu: true
                }
            ]
        }
    },

    methods: {
        selectMenu(listItem) {
            if(listItem.withSubMenu ) {
                this.$emit('select-menu', listItem.id)
            }
        }
    }
}
</script>