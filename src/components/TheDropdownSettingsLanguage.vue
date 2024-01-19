<template>
    <DropdownSettingsHeader title="Choose your language" @back="$emit('select-menu', 'main')"></DropdownSettingsHeader>
    <section class="py-2">
        <ul class="max-h-96 overflow-auto">
            <DropdownSettingListItem 
                v-for="(languageName, languageId) in languages" 
                :key="languageId" :label="languageName"
                :active="languageId === selectedOptions.languageId"
                @click="selectOption(languageId)"
                >
            </DropdownSettingListItem>
        </ul>
    </section>
</template>

<script>
import DropdownSettingListItem from './DropdownSettingListItem.vue'
import DropdownSettingsHeader from './DropdownSettingsHeader.vue'

export default {
    components: { DropdownSettingListItem, DropdownSettingsHeader },

    props: ['selectedOptions'],

    emits: ['select-menu', 'select-option'],

    data() {
        return {
            selectedLanguageId: 0,
            languages: ['English', 'Russian']
        }
    },

    methods: {
        selectOption (languageId) {
            this.$emit('select-option', { name: 'languageId', value: languageId })
        }
    }
}
</script>