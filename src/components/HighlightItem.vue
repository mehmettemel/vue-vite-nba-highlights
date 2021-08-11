<template>
    <div
        class="
            overflow-hidden
            shadow-lg
            rounded-lg
            h-full
            w-60
            md:w-80
            cursor-pointer
            m-auto
        "
    >
        <a :href="highlight.url" class="w-full block h-full">
            <div v-if="highlight.thumbnail">
                <img
                    alt="blog photo"
                    :src="highlight.thumbnail"
                    class="max-h-40 w-full object-cover"
                />
            </div>
            <div v-else>
                <img
                    alt="blog photo"
                    src="https://i.picsum.photos/id/876/200/300.jpg?hmac=goKRzVFKqeXwTjZFK6d58HDkfv32_d-P_bPCS3Mtlf4"
                    class="max-h-40 w-full object-cover"
                />
            </div>

            <div class="bg-white dark:bg-gray-800 w-full p-4">
                <p class="text-indigo-500 text-md font-medium">Article</p>
                <p
                    class="
                        text-gray-800
                        dark:text-white
                        text-xl
                        font-medium
                        mb-2
                    "
                >
                    {{ highlight.title }}
                </p>
            </div>
        </a>
    </div>
</template>

<script setup>
import { defineProps } from 'vue'
const props = defineProps({
    highlight: {
        type: Object,
        required: true,
    },
})
</script>

<style lang="scss" scoped></style>
