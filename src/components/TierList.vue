<script setup lang="ts">
import tierListData from '../data/tierlist.json'
import { useSearch } from '../composables/useSearch'
import { computed } from 'vue'

interface Source {
    name: string
    label: string | null
}

interface Tier {
    description: string
    sources: Source[]
}

const data: { tiers: Record<string, Tier> } = tierListData
const { searchQuery } = useSearch()

const filteredTiers = computed(() => {
    const query = searchQuery.value.toLowerCase().trim()

    if (!query) return data.tiers

    const filteredData: Record<string, Tier> = {}

    Object.entries(data.tiers).forEach(([tierName, tier]) => {
        const filteredSources = tier.sources.filter(
            (source) =>
                source.name.toLowerCase().includes(query) ||
                (source.label && source.label.toLowerCase().includes(query))
        )

        if (filteredSources.length > 0) {
            filteredData[tierName] = {
                ...tier,
                sources: filteredSources,
            }
        }
    })

    return filteredData
})
</script>

<template>
    <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8 py-8">
        <div
            v-for="(tier, tierName) in filteredTiers"
            :key="tierName"
            class="mb-8"
        >
            <div
                class="border-b border-gray-200 bg-white px-4 py-5 sm:px-6 rounded-t-lg"
            >
                <h3 class="text-lg font-bold text-gray-900">
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
                            <div class="font-faustina text-gray-900">
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
        <div
            v-if="Object.keys(filteredTiers).length === 0"
            class="text-center py-8 bg-gray-200 rounded"
        >
            <p class="text-gray-500">
                No results found for "{{ searchQuery }}"
            </p>
        </div>
    </div>
</template>
