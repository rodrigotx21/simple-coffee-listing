<template>
    <h1 class="pill">Popular</h1>
</template>

<script>
export default {
    name: "PopularPill"
}
</script>

<style scoped>
    .pill {
        font-size: 10px;
        width: fit-content;
        color: var(--foreground);
        background-color: var(--popular);
        padding: 2px 8px;
        border-radius: 50px;

        z-index: 1;
        position: absolute;
        margin: 10px;
    }
</style>