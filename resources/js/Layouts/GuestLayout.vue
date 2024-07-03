<script setup>
import ApplicationLogo from '@/Components/ApplicationLogo.vue';
</script>

<template>
    <div class="min-h-screen flex flex-col sm:justify-center items-center main-background">
        <div class="main-card">
            <div class="container-logo">
                <ApplicationLogo class="fill-current logo" />
            </div>
            <div class="mini-card"></div>

            <div class="card-background">
                <slot></slot>
            </div>
        </div>
    </div>
</template>

<style scoped>
    .main-background {
        background-color: var(--mix-100);
    }
    .main-card {
        position: relative;
        border-radius: 12px;

        display: flex;
        flex-direction: column;
        justify-content: flex-end;
        height: 520px;
    }
    .card-background {
        width: 452px;
        height: 433px;
        border-radius: 12px;

        display: flex;
        flex-direction: column;
        justify-content: center;

        background-color: #39342B;
    }
    .container-logo {
        position: absolute;

        top: 13px;
        left: 50%;
        transform: translateX(-50%);
        z-index: 2;
    }
    .logo {
        width: 210px;
        height: 128px;
    }
    .mini-card {
        position: absolute;

        top: 50px;
        left: 50%;
        transform: translateX(-50%);

        width: 225px;
        height: 95px;
        border-radius: 12px;
        background-color: #241F16;
        z-index: 1;
    }

    /* @media (min-width: 1920px) and (min-height: 1080px) {
        .card-background {
            width: 552px;
            height: 563px;
        }
        .logo {
            width: 248px;
            height: 152px;
        }
    } */
</style>
