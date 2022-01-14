<template>
  <div id="beerDetailsScreen">
    <ul v-for="beer in beerList" v-bind:key="beer.id">
      <li>{{ beer.name }}</li>
      <li>{{ beer.tagline }}</li>
      <img :src="beer.image_url" />
      <li>{{ beer.abv }} %</li>
      <li>{{ beer.description }}</li>
      <li>{{ beer.method }}</li>
      <li>{{}}</li>
      <li>{{}}</li>
     <!--  <button @click="showBeer(beer.id)">Read more</button> -->
    </ul>
  </div>
</template>

<script>

export default {
  name: "BeerDetailsScreen", // Skal den hete App eller BeerDetailsScreen?
  props: ['beer'],
  
};

// Jeg tok vekk data
</script>
