<script setup lang="ts">
import tierListData from '../data/tierlist.json'

interface Source {
    name: string
    label: string | null
}

interface Tier {
    description: string
    sources: Source[]
}

const data: { tiers: Record<string, Tier> } = tierListData
</script>

<template>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <div
            v-for="(tier, tierName) in data.tiers"
            :key="tierName"
            class="mb-8"
        >
            <div
                class="border-b border-gray-200 bg-white px-4 py-5 sm:px-6 rounded-t-lg"
            >
                <h3 class="text-lg font-semibold text-gray-900">
                    {{ tierName }}
                </h3>
                <p class="mt-1 text-sm text-gray-500">{{ tier.description }}</p>
            </div>

            <div class="bg-white shadow overflow-hidden sm:rounded-b-lg">
                <ul class="divide-y divide-gray-200">
                    <li
                        v-for="source in tier.sources"
                        :key="source.name"
                        class="px-4 py-4 sm:px-6 hover:bg-gray-50 transition-colors"
                    >
                        <div class="flex items-center justify-between">
                            <div class="text-sm font-medium text-gray-900">
                                {{ source.name }}
                            </div>
                            <div
                                v-if="source.label"
                                class="text-sm text-gray-500"
                            >
                                {{ source.label }}
                            </div>
                        </div>
                    </li>
                </ul>
            </div>
        </div>
    </div>
</template>
