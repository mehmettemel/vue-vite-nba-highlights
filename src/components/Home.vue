<template>
    <layout-component>
        <h1 class="mb-6 text-3xl font-bold my-6 text-center">NBA Highlights</h1>
        <div
            v-if="videos.length === 0"
            class="max-w-xl mx-auto flex justify-center items-center my-20"
        >
            <div class="spinner">
                <div class="rect1"></div>
                <div class="rect2"></div>
                <div class="rect3"></div>
                <div class="rect4"></div>
                <div class="rect5"></div>
            </div>
        </div>
        <div
            class="
                grid grid-cols-1
                md:grid-cols-2
                xl:grid-cols-3
                gap-6
                max-w-6xl
                mx-auto
            "
        >
            <div v-for="video in videos" :key="video.name">
                <highlight-item :highlight="video"></highlight-item>
            </div>
        </div>
        <div v-if="videos.length !== 0" class="max-w-lg mx-auto my-6">
            <button
                @click="loadMore"
                type="button"
                class="
                    py-2
                    px-4
                    flex
                    justify-center
                    items-center
                    bg-green-500
                    hover:bg-green-700
                    focus:ring-green-500 focus:ring-offset-green-200
                    text-white
                    w-full
                    transition
                    ease-in
                    duration-200
                    text-center text-base
                    font-semibold
                    shadow-md
                    focus:outline-none focus:ring-2 focus:ring-offset-2
                    rounded-full
                "
            >
                <svg
                    xmlns="http://www.w3.org/2000/svg"
                    class="h-6 w-6 mr-2"
                    fill="none"
                    viewBox="0 0 24 24"
                    stroke="currentColor"
                >
                    <path
                        stroke-linecap="round"
                        stroke-linejoin="round"
                        stroke-width="2"
                        d="M5 12h.01M12 12h.01M19 12h.01M6 12a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0zm7 0a1 1 0 11-2 0 1 1 0 012 0z"
                    />
                </svg>
                Load More
            </button>
        </div>
    </layout-component>
</template>

<script setup>
import { useStore } from 'vuex'
import { computed } from 'vue'
import HighlightItem from './HighlightItem.vue'
import LayoutComponent from './Layout-Component.vue'
const store = useStore()
store.dispatch('getHighlights')
const videos = computed(() => {
    return store.state.highlights.videos
})
function loadMore() {
    store.dispatch('getHighlights')
}
</script>
