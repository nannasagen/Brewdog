<template>
  <div id="beerDetailsScreen">
    <div v-if="beer !== null">
      {{ beer.name }}
      {{ beer.tagline }}
      {{ beer.abv }} %
      {{ beer.description }}
      {{ beer.method }}
      <ul v-for="(ingredient,index) in allIngredients" v-bind:key="index">
        <li>
            {{ ingredient.name }} 
          
            <span v-if="ingredient.isDone">DONE <button  @click="setDone(index, false)">IDLE</button></span>
            <span v-else>IDLE <button  @click="setDone(index, true)">DONE</button></span>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: "BeerDetailsScreen", 
  props: ["beer"],
  methods:{
    setDone(index, value){
      let ingredient = this.allIngredients[index];
      ingredient.isDone = value;
      console.log(ingredient);
    }
  },
  computed: {
    allIngredients() {
      let list = this.beer.ingredients.malt.concat(this.beer.ingredients.hops);
      console.log(list);
      return list;
    },
  },
};

</script>
