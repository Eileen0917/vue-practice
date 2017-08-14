<template>
  <div id="app">
  <form>
    <fieldset>
      <legend>Choose</legend>
        <select v-model="clan">
          <option v-for="(types, clan) in clans">{{clan}}</option>
        </select>

        <select v-model="type">
          <option v-for="(species, type) in clans[clan]">{{type}}</option>
        </select>

        <select v-if="clans[clan]">
          <option v-for="(animals,species) in clans[clan][type]">{{species}}</option>
        </select>
    </fieldset>
  </form>
  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      clan: undefined,
      type: undefined,
      clans: {
        mammalia: {
          'have fingers': {
            human: 'human',
            chimpanzee: 'chimpanzee'
          },
          'fingerless': {
            cat: 'cat',
            bear: 'bear'
          }
        },
        birds: {
          'flying': {
            eagle: 'eagle',
            pidgeon: 'pidgeon'
          },
          'non flying': {
            chicken: 'chicken'
          }
        }
      },
    }
  },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.zoom-enter-active{
  transform: scale(5);
  transition: opacity 5s;
}
p {
  transition: all 3s
}
.fade-enter-active, .fade-leave-active {
  transition: opacity .5s
}

.fadr-enter, .fade-leave-active{
  opacity: 0
}
.card{
  position: relative;
  background-color: FloralWhite;
  width: 9em;
  height: 9em;
  margin: 0.5em;
  padding: 0.5em;
  font-family: sans-serif;
  box-shadow: 0px 0px 10px 2px rgba(0,0,0,0.3);
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
