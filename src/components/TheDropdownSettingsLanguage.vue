<template>
    <DropdownSettingsHeader title="Choose your language" @back="$emit('close')"></DropdownSettingsHeader>
    <section class="py-2">
        <ul class="max-h-96 overflow-auto">
            <DropdownSettingListItem 
                v-for="(languageName, languageId) in languages" 
                :key="languageId" :label="languageName"
                :active="languageId === selectedOptions.language.id"
                @click="selectOption({id:languageId, text: languageName})"
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

    emits: ['close', 'select-option'],

    data() {
        return {
            languages: ['English', 'Russian']
        }
    },

    methods: {
        selectOption (language) {
            this.$emit('select-option', { name: 'language', value: language })
        }
    }
}
</script>