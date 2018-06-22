<template>
  <div id="app">
    <Recursive v-bind:clase="model" v-model="model"/>
    <button @click="ver" v-on:cambios="cambios">VEr como va</button>
    <pre>
      {{model}}
    </pre>
  </div>
</template>

<script>
import Recursive from "./components/Recursive";
export default {
  name: "app",
  data() {
    return {
      model: {
        nombre: "RepresentatesMatricula",
        estructura: {}
      }
    };
  },
  components: {
    Recursive
  },
  methods: {
    ver() {
      console.log(this.model);
    },
    cambios(cosa) {
      console.log(cosa);
      this.model = cosa;
    }
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.clase1 {
  background-color: red;
}
.clase2 {
  background-color: green;
}
.clase3 {
  background-color: blue;
}
.clase4 {
  background-color: aqua;
}
.clase11 {
  background-color: blueviolet;
}
</style>
