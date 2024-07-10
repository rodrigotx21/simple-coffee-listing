<template>
    <div class="rating" v-if="votes">
        <div class="star filled"></div>
        <p>{{ rating }} <span>({{ votes }} votes)</span></p>
    </div>
    <div class="rating" v-if="!votes">
        <div class="star not_filled"></div>
        <p><span>No Ratings</span></p>
    </div>
</template>

<script>
export default {
    name: "RatingStar",
    props: {
        rating: {
            type: Number,
            required: true
        },
        votes: {
            type: Number,
            required: true
        },
        computed: {
            starClass() {
                return this.votes == 0 ? 'not_filled' : 'filled';
            }
        }
    }
}
</script>

<style scoped>
    .star {
        width: 24px;
        height: 24px;
    }
    .filled {
        background-image: url("../assets/Star_fill.svg");
    }
    .not_filled {
        background-image: url("../assets/Star.svg");
    }

    .rating {
        display: flex;
        gap: 5px;
        width: fit-content;
    }

    p {
        margin: 0;
        color: #fff;
    }

    span { color: var(--button); }
</style>