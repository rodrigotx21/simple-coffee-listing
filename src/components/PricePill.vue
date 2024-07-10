<template>
    <h1>{{ price }}</h1>
</template>

<script>
export default {
    name: "PricePill",
    props: {
        price: {
            type: String,
            required: true
        }
    }
}
</script>

<style scoped>
    h1 {
        font-size: 12px;
        width: fit-content;
        height: fit-content;
        color: var(--foreground);
        background-color: var(--secondary);
        padding: 2px 8px;
        border-radius: 4px;
    }
</style>