<template>
    <button :class="{ active: isActive }">{{ text }}</button>
</template>

<script>
export default {
    name: 'CustomButton',
    props: {
        text: {
            type: String,
            required: true
        },
        isActive: {
            type: Boolean,
            default: false
        }
    }
}
</script>

<style scoped>
    button {
        height: fit-content;
        width: fit-content;
        padding: 10px 20px;
        
        border: none;
        background: transparent;
        border-radius: 8px;
        cursor: pointer;

        color: var(--accent);
        font-size: 14px;
        font-weight: 600;
    }

    button.active {
        background-color: var(--button);
    }
</style>