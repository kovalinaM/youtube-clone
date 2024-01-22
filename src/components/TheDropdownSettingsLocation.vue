<template>
    <DropdownSettingsHeader title="Choose your location" @back="$emit('close')"></DropdownSettingsHeader>
    <section class="py-2">
        <ul class="max-h-96 overflow-auto">
            <DropdownSettingListItem
                v-for="locationName, locationId in locations" 
                :key="locationId" 
                :label="locationName"
                :active="locationId === selectedOptions.location.id"
                @click="selectOption({id: locationId, text: locationName})"
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

    props:['selectedOptions'],

    emits: ['close', 'select-option'],

    data() {
        return {
            locations: ['United States', 'Russia']
        }
    },

    methods: {
        selectOption (location) {
            this.$emit('select-option', { name: 'location', value: location })
        }
    }
}
</script>