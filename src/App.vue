<template>
    <img src="./assets/bg-cafe.jpg" alt="bg-cafe">
    <div class="foreground">
        <PageHeading @changeFilter="changeFilter($event)" :allItems="allItems"/>
        <div class="cards">
            <CoffeeCard v-for="coffee in filteredCoffeeData"
                :key="coffee.id"
                :image_src="coffee.image"
                :coffee_name="coffee.name"
                :price="coffee.price"
                :rating="coffee.rating"
                :votes="coffee.votes"
                :popular="coffee.popular"
                :available="coffee.available"
            />
        </div>
    </div>
</template>


<script>
import PageHeading from "./components/PageHeading.vue"
import CoffeeCard from "./components/CoffeeCard.vue";

export default {
    name: 'App',
    components: {
        PageHeading,
        CoffeeCard
    },
    data() {
        return {
            coffee_data: [],
            allItems: true
        };
    },
    created() {
        this.fetchData();
    },
    computed: {
        filteredCoffeeData() {
            if (this.allItems) {
                return this.coffee_data;
            } else {
                return this.coffee_data.filter(coffee => coffee.available);
            }
        }
    },
    methods: {
        async fetchData() {
            try {
                const response = await fetch('https://raw.githubusercontent.com/devchallenges-io/web-project-ideas/main/front-end-projects/data/simple-coffee-listing-data.json');
                const data = await response.json();
                this.coffee_data = data;
            } catch (error) {
                console.error(error);
            }
        },

        changeFilter(newVal) {
            this.allItems = newVal;
        }
    }
}
</script>

<style>
    body {
        margin: 0;
    }

    #app {
        height: max(100vh, fit-content);
        display: flex;
        flex-direction: column;
        align-items: center;
        justify-content: flex-start;

        background: var(--background);
    }

    img[alt="bg-cafe"] {
        width: 100%;
        height: auto;
    }

    .foreground {
        width: 90%;
        height: fit-content;
        margin-top: -160px;
        margin-bottom: 60px;
        padding: 80px 100px;
        box-sizing: border-box;

        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 40px;

        border-radius: 16px;
        background: var(--foreground);
    }

    .cards {
        width: 90%;
        display: flex;
        justify-content: center;
        flex-wrap: wrap;
        gap: 40px;
    }
</style>
