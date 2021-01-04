<template>
  <div id="pokemon">
      <h1>{{num}} - {{name | upper}}</h1>
      <small>{{url}}</small>
  </div>
</template>

<script>
export default {
props:{
    num: Number,
    name: String,
    url: String
},
filters:{
    upper: function(valor){
        var newValor = valor[0].toUpperCase() + valor.slice(1);
        return newValor;
    }
}
}
</script>

<style>

</style>