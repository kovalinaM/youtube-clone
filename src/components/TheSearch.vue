<template>
    <div class="flex w-full mr-2">
        <div class="relative flex w-full">
            <TheSearchInput 
                v-model:query="query" 
                :has-results="results.length" 
                @update:query="updateSearchResults"
                @change-state="toggleSearchResults"             
                @keyup.up="handlePreviousSearchResult"
                @keyup.down="handleNextSearchResult"
                @keydown.up.prevent />
            <TheSearchResults v-show="isSearchResultsShown" :results="results" :active-result-id="activeSearchResultId"/>
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

    props: ['searchQuery'],

    emits: ['update-search-query'],

    data() {
        return {
            results: [],
            query: this.searchQuery,
            activeQuery: this.searchQuery,
            isSearchResultsShown: false,
            activeSearchResultId: null,
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
        trimedQuery() {
            return this.query.replace(/\s+/g, ' ').trim();
        }
    },

    watch: {
        query(query) {
            this.$emit('update-search-query', query)
        }
    },

    methods: {
        updateSearchResults() {
            this.activeSearchResultId = null
            this.activeQuery = this.query

            if (this.query === '') {
                this.results = []
            } else {
                this.results = this.keywords.filter(result => {
                return result.includes(this.trimedQuery);
            })
            }
        },

        toggleSearchResults(isSearchInputActive) {
            this.isSearchResultsShown = isSearchInputActive && this.results.length
        },

        handlePreviousSearchResult() {
            if(this.isSearchResultsShown) {
                this.makePreviousSearchActive()
            } else {
                this.toggleSearchResults(true)
            }
        },

        handleNextSearchResult() {
            if(this.isSearchResultsShown) {
                this.makeNextSearchActive()
            }else {
                this.toggleSearchResults(true)
            }
        },

        makePreviousSearchActive() {
            if(this.activeSearchResultId === null) {
                this.activeSearchResultId = this.results.length -1
            } else if(this.activeSearchResultId === 0) {
                this.activeSearchResultId = null
            } else {
                this.activeSearchResultId--
            }

            this.updateQueryWithSearchResult()
        },

        makeNextSearchActive() {
            if(this.activeSearchResultId === null) {
                this.activeSearchResultId = 0
            } else if(this.activeSearchResultId + 1 === this.results.length) {
                this.activeSearchResultId = null
            } else{
                this.activeSearchResultId++
            }

            this.updateQueryWithSearchResult()
        },

        updateQueryWithSearchResult() {
            const hasActiveSearchResult = this.activeSearchResultId != null

            this.query = hasActiveSearchResult ? this.results[this.activeSearchResultId] : this.activeQuery
        }
    }
}
</script>