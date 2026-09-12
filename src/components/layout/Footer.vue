<script setup>
    import { computed } from 'vue';
    import { useVersionStore } from '../../stores/version';
    import packageJson from '../../../package.json';

    defineProps({
        hideBranding: {
            type: Boolean,
            default: false,
        },
    });

    const versionStore = useVersionStore();
    const currentYear = computed(() => new Date().getFullYear());
    const currentVersion = packageJson.version;
</script>

<template>
    <footer class="w-full text-center p-8 border-t border-gray-200 dark:border-white/10 mt-8">
        <div
            class="flex flex-col sm:flex-row items-center justify-center gap-2 text-xs text-gray-400 dark:text-gray-500"
        >
            <p>Copyright © {{ currentYear }} 小卢机场. All Rights Reserved.</p>
            <button
                @click="versionStore.openModal"
                class="px-1.5 py-0.5 rounded bg-gray-100 dark:bg-white/5 text-[9px] font-mono hover:text-indigo-500 dark:hover:text-indigo-400 transition-colors cursor-pointer opacity-80 hover:opacity-100 border border-transparent hover:border-indigo-500/30"
            >
                v{{ currentVersion }}
            </button>
        </div>
    </footer>
</template>
