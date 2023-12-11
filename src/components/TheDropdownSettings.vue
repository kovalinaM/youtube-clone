<template>
    <div class="opacity-0 group-hover:opacity-100 absolute top-9 -right-full sm:right-0 bg-white w-72 border border-t-0">
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
</template>

<script>
import DropdownSettingListItem from './DropdownSettingListItem.vue'
import BaseIcon from './BaseIcon.vue'

export default {
    components: { DropdownSettingListItem, BaseIcon },
    data() {
        return {
            listItems: [
                {
                    label: 'Appearance: Light',
                    icon:'sun',
                    withSubMenu: true
                },
                {
                    label: 'Language: English',
                    icon:'translate',
                    withSubMenu: true
                },
                {
                    label: 'Location: Russia',
                    icon:'globeAlt',
                    withSubMenu: true
                },
                {
                    label: 'Settings',
                    icon:'cog',
                    withSubMenu: false
                },
                {
                    label: 'Your data in YouTube',
                    icon:'shieldCheck',
                    withSubMenu: false
                },
                {
                    label: 'questionMarkCircle',
                    icon:'help',
                    withSubMenu: false
                },
                {
                    label: 'Keyboard shortcuts',
                    icon:'calculator',
                    withSubMenu: false
                }
            ]
        }
    }
}
</script>