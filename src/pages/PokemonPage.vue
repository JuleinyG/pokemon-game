<template>
    <h1 v-if="!pokemon">Espere por favor...</h1>
    <div v-else> 
      <div class="grapper">
            <h1>¿Quién es este pokémon?</h1>

            <PokemonPicture 
            :pokemonId="pokemon.id" 
            :show-pokemon="showPokemon"
            />

            <PokemonOptions 
            :pokemons="pokemonArr"
            @selection-pokemon="checkAnswer" 
            />

        
        <div v-if="showAnswer" class="div">
                <h2 class="fade-in">{{ message }}</h2>
                <button @click="newGame"
                class="button">
                    Nuevo juego
                </button>
        </div>
      </div>
    </div>
</template>

<script>
import PokemonOptions from '@/components/PokemonOptions'
import PokemonPicture from '@/components/PokemonPicture'

import getPokemonOptions from '@/helpers/getPokemonOptions'

//console.log(getPokemonOptions())

export default {
    components:{ PokemonOptions, PokemonPicture},
    data() {
     return{
         pokemonArr: [],
         pokemon: null,
         showPokemon:false,
         showAnswer: false,
         message: ''
     }
    },
    methods:{
        async mixPokemonArray() {
            this.pokemonArr= await getPokemonOptions()
            
            const rndInt = Math.floor( Math.random() * 4 )
            this.pokemon = this.pokemonArr[ rndInt ]
        },
        checkAnswer( selecteId ) {
            this.showPokemon = true
            this.showAnswer = true

            if( selecteId === this.pokemon.id ) {
                this.message = `Correcto, ${ this.pokemon.name }`
            } else {
                this.message = `Oops, era ${ this.pokemon.name }`
            }
        },
        newGame() {

            this.showPokemon = false
            this.showAnswer = false
            this.pokemonArr = []
            this.pokemon = null
            this.mixPokemonArray()

        }
    },
    mounted(){
        this.mixPokemonArray()
    }
}
</script>

<style scoped>
.button{
    background-color: rgb(166, 221, 223);
    font-size: 19px;
    padding: 5px;
    border-color: rgb(216, 242, 248);
    border-radius: 5px;
    cursor: pointer;
    width: 290px;
}
.grapper {
    flex-direction: column;
    display: flex;
    align-items: center;
    justify-content: center;
    
}
</style>