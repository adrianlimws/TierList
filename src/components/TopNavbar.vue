<script setup lang="ts">
import logo from '../assets/tierlist.svg'
</script>

<template>
    <nav class="bg-white shadow">
        <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
            <div class="flex h-16 items-center">
                <div class="h-8 w-8">
                    <img
                        :src="logo"
                        alt="Logo"
                        class="h-full w-full object-contain"
                    />
                </div>
                <h1 class="text-xl font-bold text-gray-900">Tier List</h1>
            </div>
        </div>
    </nav>
</template>
