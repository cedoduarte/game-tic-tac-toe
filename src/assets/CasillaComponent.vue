<template>
    <button>{{ figura }}</button>
</template>

<script setup lang="ts">
import { defineProps } from "vue";

defineProps({
    figura: String
});
</script>

<style scoped>
button {
    width: 100px;
    height: 100px;
    font-size: 50px;
    background-color: transparent;
    border-color: #42b883;
    margin: 5px;
}
</style>