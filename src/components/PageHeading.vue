<template>
    <div class="PageHeading">
        <h1>Our Collection</h1>
        <p>Introducing our Coffee Collection, a selection of unique coffees from different roast 
            types and origins, expertly roasted in small batches and shipped fresh weekly.</p>
        <div class="selector">
            <CustomButton v-for="(button, index) in buttons"
                :key="index"
                :isActive="activeButtonIndex == index"
                @click="setActiveButton(index, button.filter)"
                :text="button.text"
            />
        </div>
    </div>
</template>

<script>
import CustomButton from "./CustomButton.vue";

export default {
    name: 'PageHeading',
    components: {
        CustomButton
    },
    data() {
        return {
            buttons: [
                { text: 'All Products', filter: false },
                { text: 'Available Now', filter: true },
            ],
            activeButtonIndex: 0
        }
    },
    props: {
        allItems: {
            type: Boolean,
            required: true,
            default: true
        }
    },
    methods: {
        setActiveButton(index, filter) {
            this.activeButtonIndex = index;
            this.$emit('changeFilter', !filter)
        }
    }
}
</script>

<style scoped>
    h1 {
        color: var(--accent);
        font-weight: 600;
        margin: 0;
    }

    p {
        color: var(--button);
        margin: 0;
        width: 100%;
        height: auto;
    }

    .PageHeading {
        width: 100%;
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 20px;

        box-sizing: border-box; /* Ensure padding is included in width */

        text-align: center;
    }

    /* Tablet */
    @media only screen and (min-width: 540px) and (max-width: 1159px) {
        .PageHeading {
            padding: 0 90px;
        }
    }

    /* Desktop */
    @media only screen and (min-width: 1160px) {
        .PageHeading {
            padding: 0 240px;
        }
    }
</style>