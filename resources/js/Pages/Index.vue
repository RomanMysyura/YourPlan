<script setup>
import { Head, Link } from '@inertiajs/vue3';
import MainMenu  from '@/Components/Menu/MainMenu.vue';

defineProps({
    canLogin: {
        type: Boolean,
    },
    canRegister: {
        type: Boolean,
    },
    laravelVersion: {
        type: String,
        required: true,
    },
    phpVersion: {
        type: String,
        required: true,
    },
});


</script>
<template>
    <Head title="YourPlan" />

    <MainMenu />

    <div>
        
        
    </div>

    <h1>test</h1>
    <h1>test</h1>
    <h1>test</h1>
    <h1>test</h1>
    <h1>test</h1>

</template>