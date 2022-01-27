<template>
  <div id="app">
    <div style="display: flex; flex-direction: row">
      <BeerListScreen
        :beers="beerList"
        @beer-selected="selectedBeer"
      ></BeerListScreen>
      <BeerDetailsScreen :beer="theBeer"></BeerDetailsScreen>
    </div>
    <div>{{ theBeer == null ? "ingenting" : theBeer.id }}</div>
  </div>
</template>

<script>
import BeerListScreen from "./components/BeerListScreen.vue";
import BeerDetailsScreen from "@/components/BeerDetailsScreen.vue";

export default {
  name: "App",
  components: {
    BeerListScreen,
    BeerDetailsScreen,
  },
  data() {
    return {
      beerList: [],
      theBeer: null,
    };
  },
  async mounted() {
    let response = await fetch("https://api.punkapi.com/v2/beers");
    let beers = await response.json();
    console.log(beers);
    for (let beer of beers) {
      for (let ingredient of beer.ingredients.hops) {
        ingredient.isDone = false;
      }
      for (let ingredient of beer.ingredients.malt) {
        ingredient.isDone = false;
      }
    }
    this.beerList.push(...beers);
  },
  methods: {
    selectedBeer(beer) {
      this.theBeer = beer;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
body {
  background-color: darkslategrey;
}
h3 {
  font-family: "Courier New", Courier, monospace;
  font-size: 40px;
  color: rgb(92, 49, 18);
}
li.nameTag {
  font-family: "Courier New", Courier, monospace;
  font-size: 45px;
  color: teal;
}
li {
  font-family: "Courier New", Courier, monospace;
  font-size: 20px;
  color: peru;
}
img {
  max-height: 160px;
  max-width: 80px;
}
div.spacialAwareness {
  color: rgb(223, 100, 12);
  margin-top: 40px;
  margin-bottom: 40px;
}
</style>
