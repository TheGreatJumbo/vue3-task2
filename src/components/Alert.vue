<template>
    <div class="alert danger">
        <p><slot></slot></p>
        <button class="btn warning" @click="$emit('TryAgain')">Попробовать снова</button>
    </div>
</template>

<script>
    export default {
        name: "Alert",
        emits: ['TryAgain']
    }
</script>

<style scoped>

</style>