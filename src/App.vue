<template>
  <div id="app">
    <div id="pokemon" v-for="(poke, index) in pokemons" :key="index" >
      <Pokemon :num=index+1 :name=poke.name :url=poke.url />
      <button class="button" @click="salvarPokemon(index+1, poke.name, poke.url)" > Salvar</button>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
import Pokemon from './components/Pokemon'

export default {
  name: 'App',
  data(){
    return{
      pokemons:[]
    }
  },
  components: {
    Pokemon
  },
  created: function(){
    axios.get("https://pokeapi.co/api/v2/pokemon?limit=151&offset=0").then(res => {
      console.log("PEGOU DA LISTA DE POKEMONS");
      this.pokemons = res.data.results;
     // console.log(this.pokemons);
    });
      
  },
  methods:{
    salvarPokemon: function(index, nome, url){

/*
      const options = {
      method: 'post',
      url: 'https://pokemons-f24aa-default-rtdb.firebaseio.com/pokemons',
      xsrfCookieName: 'XSRF-TOKEN',
      xsrfHeaderName: 'X-XSRF-TOKEN',
    };

    // send the request
    axios(options);  */

      console.log("ID:" + index + " NOME: " + nome + " URL: " + url);
      axios.post('https://pokemons-f24aa-default-rtdb.firebaseio.com/pokemons', {id: 'index', nome: 'nome', url: 'url'});
    }
  }
}
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
</style>
