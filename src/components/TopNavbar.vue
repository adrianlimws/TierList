<script setup lang="ts">
import logo from '../assets/tierlist.svg'
import { useSearch } from '../composables/useSearch'
const { searchQuery } = useSearch()
</script>

<template>
    <nav class="bg-white shadow">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex h-16 items-center justify-between">
                <h1
                    class="text-xl font-bold text-gray-900 flex items-center uppercase"
                >
                    <img
                        :src="logo"
                        alt="Logo"
                        class="h-8 w-8 object-contain mr-3"
                    />
                    Tier List
                </h1>
                <div class="flex-1 max-w-lg mx-4">
                    <div class="relative">
                        <input
                            type="text"
                            v-model="searchQuery"
                            placeholder="Search sources..."
                            class="w-full px-4 py-2 rounded-lg border border-gray-300 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
                        />
                    </div>
                </div>
                <p class="text-sm text-gray-400">
                    Modified from Original Source:
                    <a
                        class="underline hover:text-red-500"
                        href="https://www.reddit.com/r/reddevils/wiki/transfer-reliability-guide/"
                        target="_blank"
                        >/r/reddevils</a
                    >
                </p>
            </div>
        </div>
    </nav>
</template>
