<template>
<div>
    <h3>Brewdog beer</h3>
    <ul v-for="beer in beerList" v-bind:key="beer.id">
        <li>
        {{beer.name}} {{beer}}
        <button @click="selectBeer(beer)">Read more</button>
        </li>
    </ul>
</div>
</template>

<script>

export default{
    name: "BeerListScreen",
    data(){

    },
    props: ['beers'],
    methods: {
        selectedBeer(beer){
            this.$emit('beer-selected', beer);
        }
    }
}
</script>