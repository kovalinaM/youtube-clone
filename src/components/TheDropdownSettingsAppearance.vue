<template>
    <DropdownSettingsHeader title="Appearance" @back="$emit('select-menu', 'main')"></DropdownSettingsHeader>
    <section class="py-2">
        <div class="text-gray-500 text-xs p-3">Setting applies to this browser only</div>
        <ul>
            <DropdownSettingListItem 
                v-for="themeName, themeId in themes" 
                :key="themeName" :label="themeName" 
                :active="themeId === selectedThemeId"
                @click="selectedThemeId = themeId">
            </DropdownSettingListItem>
        </ul>
    </section>
    <!-- <section class="py-2">
        <ul>
            <DropdownSettingListItem label="Restricted Mode: Off" with-sub-menu></DropdownSettingListItem>
        </ul>
    </section> -->
</template>

<script>
import DropdownSettingListItem from './DropdownSettingListItem.vue'
import DropdownSettingsHeader from './DropdownSettingsHeader.vue'

export default {
    components: { DropdownSettingListItem, DropdownSettingsHeader },

    emits: ['select-menu'],

    data() {
        return {
            selectedThemeId: 0,
            themes: ['Use device theme', 'Dark theme', 'Light theme'
            ]
        }
    },
}
</script>