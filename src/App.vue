<template>
  <div id="app">
    <button @click="taxiCalled = true">
      call a cab
    </button>
    <button @click="taxiCalled = false">
      Cancel
    </button>
    <transition
      @enter="enter"
      @leave="leave"
      :css="false"
    >
      <p v-if="taxiCalled">🚕</p>
    </transition>

  </div>
</template>

<script>
export default {
  name: 'app',
  data: function () {
    return {
      taxiCalled: false
    }
  },
  methods: {
    enter (e1) {
      Velocity(e1,
      { opacity: [1, 0], translateX: ["0px", "200px"] },
      { duration: 2000, easing: "ease-out" } )
    },
    leave (e1, done) {
      Velocity(e1,
      { opacity: [0, 1], 'font-size': ['0.1em', '1em'] },
      { duration: 2000, complete: done } )
    }
  }
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
