<template>
    <DropdownSettingsHeader title="Choose your location" @back="$emit('select-menu', 'main')"></DropdownSettingsHeader>
    <section class="py-2">
        <ul class="max-h-96 overflow-auto">
            <DropdownSettingListItem
                v-for="locationName, locationId in locations" 
                :key="locationId" 
                :label="locationName"
                :active="locationId === selectedOptions.locationId"
                @click="selectOption(locationId)"
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

    emits: ['select-menu', 'select-option'],

    data() {
        return {
            selectedLocationId: 0,
            locations: ['United States', 'Russia']
        }
    },

    methods: {
        selectOption (locationId) {
            this.$emit('select-option', { name: 'locationId', value: locationId })
        }
    }
}
</script>