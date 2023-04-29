<script setup lang='ts'>
import { computed } from 'vue';

interface Props {
    shimmerColor?: string
    bgColor?: string
}

const props = withDefaults(defineProps<Props>(), {
    shimmerColor: '#FFFFFF',
    bgColor: '#9CA3AF'
});


const hexToRgb = (hex: string) => `${hex.match(/\w\w/g)?.map((x) => +`0x${x}`)}`;

const shimmerStyle = computed(() => {
    const rgb = hexToRgb(props.shimmerColor)

    return {
        backgroundImage: `linear-gradient(90deg, rgba(${rgb}, 0) 0%, rgba(${rgb}, 0.2) 20%, rgba(${rgb}, 0.5) 60%, rgba(${rgb}, 0))`,
    };
});

</script>

<template>
    <div :class="['relative overflow-hidden']" :style="{
            backgroundColor: bgColor
        }">
        <div class="shimmer absolute inset-0" :style="shimmerStyle">
        </div>
        <slot />
    </div>
</template>

<style scoped>
.shimmer {
    transform: translateX(-100%);
    animation: shimmer 1.4s infinite;
}

@keyframes shimmer {
    100% {
        transform: translateX(100%);
    }
}
</style>