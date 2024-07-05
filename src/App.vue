<script setup>
import CountDown from './components/CountDown.vue';
import Background from './components/Background.vue';
</script>

<template>
    <main>
        <Background></Background>
        <CountDown end-time="2024/8/20 10:00:00"></CountDown>
    </main>
</template>