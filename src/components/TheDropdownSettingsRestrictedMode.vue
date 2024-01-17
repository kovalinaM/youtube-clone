<template>
    <DropdownSettingsHeader title="Choose your location" @back="$emit('select-menu', 'main')"></DropdownSettingsHeader>
    <section class="py-2">
        <p>This helps hide potentially mature videos. No filter is 100% accurate.</p>
        <p>This setting omly applies to this browser.</p>
        <div>
            <span>Activate restricted mode</span>
            <input type="checkbox">
        </div>
    </section>
</template>

<script>
import DropdownSettingsHeader from './DropdownSettingsHeader.vue'

export default {
    components: { DropdownSettingsHeader },

    emits: ['select-menu'],
}
</script>