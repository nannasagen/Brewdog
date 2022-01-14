<template>
  <div id="beerDetailsScreen">
    <ul v-if="beer !== null">
      <li>{{ beer.name }}</li>
      <li>{{ beer.tagline }}</li>
      <img :src="beer.image_url" />
      <li>{{ beer.abv }} %</li>
      <li>{{ beer.description }}</li>
      <ul>
        <li>{{ beer.method }} <button @click="buttonPressed()">'${buttonState}'</button></li>
        <li>{{ beer.brewing_tips }}</li>
        <li>{{beer.malts}}</li>
        <li>{{beer.hops}}</li>
      </ul>
    </ul>
  </div>
</template>

<script>
export default {
  name: "BeerDetailsScreen",
  props: ["beer"],
  methods:{
    buttonPressed(){
      
    }
  },
};

// Jeg tok vekk data
</script>
