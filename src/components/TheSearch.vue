<template>
    <div class="flex w-full h-full">
        <TheSearchInput></TheSearchInput>
        <TheSearchButton></TheSearchButton>
    </div>
</template>

<script>
import TheSearchInput from './TheSearchInput.vue'
import TheSearchButton from './TheSearchButton.vue'

export default {
    components: { TheSearchInput, TheSearchButton }
}
</script>