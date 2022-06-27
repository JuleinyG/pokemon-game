<template>
  <div class="grapper-test">
    <div class="pokemon-container">
        <img :src="imgSrc" 
                class="hidden-pokemon"
                alt="pokemon">
        <img v-if="showPokemon"
                :src="imgSrc" 
                class="fade-in"
                alt="pokemon">
    </div>
  </div>

</template>

<script>
export default {

    props:{
        pokemonId: {
            type:Number,
            required:true
        },
        showPokemon: {
            type:Boolean,
            required:true,
            default: false
        }
    },

    computed:{
        imgSrc() {
            return `https://raw.githubusercontent.com/PokeAPI/sprites/master/sprites/pokemon/other/dream-world/${ this.pokemonId }.svg`
        }
    }

}
</script>

<style scoped>
/* Pokemon Picture */
.pokemon-container {
    height: 200px;
}
img {
    height: 200px;
    position: absolute;
    margin-left: auto;
    margin-right: auto;
    left: 0;
    right: 0;
    text-align: center;
    vertical-align: middle;
    -moz-user-select: none;
    -ms-user-select: none;
    -webkit-user-drag: none;
    -webkit-user-select: none;
}
.hidden-pokemon {
    filter: brightness(0);
}

.grapper-test {
    display: flex;
    align-items: center;
    justify-content: center;
}

/* s */

</style>