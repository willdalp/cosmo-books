<script setup>
defineProps({
    value: {
        type: String,
    },
});
</script>

<template>
    <label class="text-white font-medium">
        <span v-if="value">{{ value }}</span>
        <span v-else><slot /></span>
    </label>
</template>
