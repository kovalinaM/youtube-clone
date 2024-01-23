<template>
    <div class="flex w-full mr-2">
        <div class="relative flex w-full">
            <TheSearchInput></TheSearchInput>
            <TheSearchResults :results="keywords"/>
        </div>
        <TheSearchButton></TheSearchButton>
    </div>
</template>

<script>
import TheSearchInput from './TheSearchInput.vue'
import TheSearchButton from './TheSearchButton.vue'
import TheSearchResults from './TheSearchResults.vue'

export default {
    components: { TheSearchInput, TheSearchButton, TheSearchResults },

    data() {
        return {
            keywords: [
                'new york',
                'new york song',
                'new york city',
                'new york new york frank sinatra',
                'new york giants live',
                'new york state of mind',
                'new york live stream',
                'new york accent',
                'new york giants',
                'new york alicia keys',
            ]
        }
    }
}
</script>