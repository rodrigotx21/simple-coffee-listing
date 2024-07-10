<template>
    <div class="Card">
        <PopularPill v-if="popular"/>
        <img :src='image_src' :alt='coffee_name'>
        <div class="frame">
            <h1 class="name">{{ coffee_name }}</h1>
            <PricePill :price="price"/>
        </div>
        <div class="frame">
            <RatingStar :rating="rating" :votes="votes"/>
            <p class="warning" v-if="!available">Sold Out</p>
        </div>
    </div>
</template>

<script>
import PopularPill from "./PopularPill.vue";
import PricePill from "./PricePill.vue"
import RatingStar from "./RatingStar.vue";

export default {
    name: 'CoffeeCard',
    components: {
        PopularPill,
        PricePill,
        RatingStar
    },
    props: {
        image_src: {
            type: String,
            required: true
        },
        coffee_name: {
            type: String,
            required: true
        },
        price: {
            type: String,
            required: true
        },
        rating: {
            type: Number,
            required: true
        },
        votes: {
            type: Number,
            required: true
        },
        popular: {
            type: Boolean,
            required: true
        },
        available: {
            type: Boolean,
            required: true
        }
    }
}
</script>

<style scoped>
    img {
        width: 260px;
        height: 160px;
        border-radius: 12px;
    }

    h1 { margin: 0; }

    .Card {
        height: fit-content;
        width: fit-content;
        display: flex;
        flex-direction: column;
        gap: 10px;
    }

    .name {
        color: #fff;
        font-size: 14px;
        font-weight: 600;
    }

    .warning {
        margin: 0;
        font-size: 12px;
        font-weight: 700;
        color: var(--warning);
    }

    .frame {
        height: fit-content;
        display: flex;
        justify-content: space-between;
        align-items: center;
    }
</style>