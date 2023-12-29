<template>
    <div class="flex w-full mr-2">
        <!-- <div class="relative flex w-full"> -->
        <TheSearchInput></TheSearchInput>
    <!-- </div> -->
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