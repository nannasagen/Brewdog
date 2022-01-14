<template>
  <div>
    <h3>Brewdog beer</h3>
    
      <ul v-for="beer in beerList" v-bind:key="beer.id">
        <div class="spacialAwareness">--------------------------------</div>

        <li>{{ beer.name }}</li>
        <br />
        <img :src="beer.image_url" />
        <br />
        <li>{{ beer.abv }} %</li>
        <br />
        <li>{{ beer.description }}</li> 
        <button @click="selectedBeer(beer.id)">Read more</button>
        
        <div class="spacialAwareness">--------------------------------</div>
      </ul>
     
  </div>
</template>

<script>
export default {
  name: "Api",
  
  props: ['beers'], // Endring + button
  
   methods: { // Endring
        selectedBeer(beer){
            this.$emit('beer-selected', beer);
        }
    }
};
</script>