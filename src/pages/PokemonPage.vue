<template>

   <h1 v-if="!pokemon"> Espere por favor...</h1>

   <div v-else>
        <h1> Quien es este pokemon?</h1>

        <PokemonPicture :pokemon-id="pokemon.id" :show-pokemon="showPokemon" />

        <PokemonLists :pokemons="pokemonArr" 
        @selection="checkAnswer($event)"/>

        <div  v-if="showAnswer">
            <h2 class="fade-in" >
                {{message}}
            </h2>

            <button @click="newGame">
                Nuevo Juego
            </button>
        </div>

   </div>

</template>

<script>

import PokemonPicture from '@/components/PokemonPicture.vue'
import PokemonLists from '../components/PokemonLists.vue'

import getPokemonOptions from '@/helpers/getPokemonOptions'
// console.log(getPokemonOptions ())

export default {
  components:{
      PokemonLists,
      PokemonPicture
  },
  data() {
      return {
          pokemonArr:[],
          pokemon: null,
          showPokemon: false,
          showAnswer: false,
          message: ''
      }
  },
    methods: {
        async mixPokemonArray() {
          this.pokemonArr =  await getPokemonOptions()

          const rndInt = Math.floor( Math.random() * 4)
          this.pokemon = this.pokemonArr [rndInt]
        //   console.log(rndInt)

     //   console.log(this.pokemonArr)
      },
      checkAnswer(selectedId){
          this.showPokemon = true
          this.showAnswer = true
          if(selectedId === this.pokemon.id){
              this.message = `Correcto,  ${ this.pokemon.name}`
          }
          else{
              this.message =  `Upps, era   ${ this.pokemon.name}`
          }
        //   console.log('llamndo a chris', ponkemonId)
      },
      newGame(){
          this.showPokemon = false
          this.showAnswer = false
          this.pokemon = null
          this.pokemonArr = []
          this.mixPokemonArray()
      }
  },
  mounted() {
        this.mixPokemonArray()
  },
 
}
</script>

