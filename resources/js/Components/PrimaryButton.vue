<template>
    <button class="primary-button">
        <slot />
    </button>
</template>

<style scoped>
    .primary-button {
        width: 100%;
        font-family: "Plus Jakarta Sans", sans-serif;
        font-weight: bold;
        font-size: 1.4rem;
        text-align: center;
        padding: 10px 0;
        background-color: var(--primary-500);
        border-radius: 0.375rem;
        color: var(--dark-200);
        transition: all 0.20s;
    }

    .primary-button:hover {
        background-color: var(--primary-300);
    }
</style>
