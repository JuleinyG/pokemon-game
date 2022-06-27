<template>
    <div class="options-container">
        <ul>
            <li v-for="pokemon in pokemons" 
                :key="pokemon.id"
                flat
                :active="active == 1" 
                @click="$emit( 'selectionPokemon', pokemon.id), active = 1 "
                >
                {{ pokemon.name }}
            </li>       
        </ul>
  </div>
</template>

<script>
export default {
    props: {
        pokemons: {
            type: Array,
            required: true
        }
    },
    methods: {
        hola(){
            //this.$emit()
        }
    },
    data:() => ({
        active: 0
    })
}
</script>

<style scoped>
/* Pokemon Options */
ul {
    list-style-type: none;
    padding: 0
}
li {
    background-color: white;
    border-radius: 5px;
    border: 1px solid rgba(0, 0, 0, 0.2);
    cursor: pointer;
    margin-bottom: 10px;
    width: 290px;
}

li:hover {
    background-color:  rgb(166, 221, 223);
}

/* .options-container {
    display: flex;
    justify-content: center;
} */
</style>