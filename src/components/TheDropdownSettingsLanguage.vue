<template>
    <DropdownSettingsHeader title="Choose your language" @back="$emit('select-menu', 'main')"></DropdownSettingsHeader>
    <section class="py-2">
        <ul>
            <DropdownSettingListItem v-for="language, languageId in languages" :key="language" :label="language"
                :active="languageId === selectedLanguageId" @click="selectedLanguageId = languageId">
            </DropdownSettingListItem>
        </ul>
    </section>
</template>

<script>
import DropdownSettingListItem from './DropdownSettingListItem.vue'
import DropdownSettingsHeader from './DropdownSettingsHeader.vue'

export default {
    components: { DropdownSettingListItem, DropdownSettingsHeader },

    emits: ['select-menu'],

    data() {
        return {
            selectedLanguageId: 0,
            languages: ['English', 'Russian']
        }
    },
}
</script>