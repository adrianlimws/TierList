<script setup lang="ts">
import logo from '../assets/tierlist.svg'
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
