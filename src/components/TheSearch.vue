<template>
    <div class="flex w-full mr-2">
        <div class="relative flex w-full">
            <TheSearchInput v-model:query="query"></TheSearchInput>
            <TheSearchResults v-show="query" :results="results"/>
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
            query: '',
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
    },

    computed: {
        results() {
            return this.keywords.filter(result => {
                return result.includes(this.query);
            })
        }
    } 
}
</script>