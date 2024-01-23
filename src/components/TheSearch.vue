<template>
    <div class="flex w-full mr-2">
        <div class="relative flex w-full">
            <TheSearchInput 
                v-model:query="query"
                @focus="isSearchInputFocused = true"
                @blur="isSearchInputFocused = false"
                />
            <TheSearchResults v-show="isSearchResultsShown" :results="results"/>
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
            isSearchInputFocused: false,
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
            if(!this.query) {
                return []
            }

            return this.keywords.filter(result => {
                return result.includes(this.trimedQuery);
            })
        },

        trimedQuery() {
            return this.query.replace(/\s+/g, ' ').trim();
        },

        isSearchResultsShown() {
            return this.isSearchInputFocused && this.results.length
        }
    } 
}
</script>