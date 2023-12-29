<template>
    <section class="py-2 border-b">
        <ul>
            <DropdownSettingListItem 
                v-for="listItem in listItems.slice(0,8)"
                :key="listItem.label" 
                :icon="listItem.icon"
                :label="listItem.label" 
                :with-sub-menu="listItem.withSubMenu"
                @click.stop="$emit('select-menu', listItem.id)"
                ></DropdownSettingListItem>
        </ul>
    </section>
    <section class="py-2">
        <ul>
            <DropdownSettingListItem 
                :label="listItems[8].label" 
                :with-sub-menu="listItems[8].withSubMenu"
                @click.stop="$emit('select-menu', listItems[8].id)"
                ></DropdownSettingListItem>
        </ul>
    </section>
</template>

<script>
import DropdownSettingListItem from './DropdownSettingListItem.vue'

export default {
    components: {DropdownSettingListItem},

    emits: ['select-menu'],

    data() {
        return {
            listItems: [
                {
                    id: 'appearance',
                    label: 'Appearance: Light',
                    icon: 'sun',
                    withSubMenu: true
                },
                {
                    id: 'language',
                    label: 'Language: English',
                    icon: 'translate',
                    withSubMenu: true
                },
                {
                    id: 'location',
                    label: 'Location: Russia',
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
                    id: 'keyboard_shortcuts',
                    label: 'Keyboard shortcuts',
                    icon: 'calculator',
                    withSubMenu: false
                }
                ,
                {
                    id: 'restricted_mode',
                    label: 'Restricted Mode: Off',
                    icon: null,
                    withSubMenu: true
                }
            ]
        }
    },
}
</script>