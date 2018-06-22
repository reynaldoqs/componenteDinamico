<template>
  <div class="main-contianer" >
    <button @click="makeIt">
      Asignar
    </button>
    <button @click="doIt">
      Crear Componente
    </button>
    <input type="text" v-model="otro.nombre" placeholder="Nombre">
    <input type="text" v-model="otro.tipo" placeholder="tipo">
    <div ref="container"></div>
  </div>
</template>
<script>
import Recursive from "./Recursive";
import Vue from "vue";

export default {
  name: "Recursive",
  data() {
    return {
      homeData: {},
      otro: {}
    };
  },
  props: {
    clase: {
      required: true,
      type: Object
    }
  } /* ,
  watch: {
    homeData(newValue, oldValue) {
      console.log(newValue);
      console.log(oldValue);
    }
  } */,
  methods: {
    makeIt() {
      this.clase[this.otro.nombre] = {
        tipo: this.otro.tipo
      };
      /*   Object.defineProperty(this.objData, [this.homeData.nombre], {
        value: {
          tipo: this.homeData.tipo,
          descripcion: this.homeData.descripcion
        },
        writable: true
      }); */
      /*       let nuevo = {
        [this.homeData.nombre]: {
          tipo: this.homeData.tipo,
          descripcion: this.homeData.descripcion
        }
      };
      Object.assign(this.objData, nuevo); */
    },
    doIt() {
      var ComponentClass = Vue.extend(Recursive);
      var instance = new ComponentClass({
        propsData: { clase: this.clase[this.otro.nombre] }
      });
      instance.$mount();
      this.$refs.container.appendChild(instance.$el);
    }
  },
  updated() {
    /* console.log("thisis my obj");
    Object.keys(this.objData).map(key => {
      console.log(key);
    }); */
  }
};
</script>
<style scoped>
.main-contianer {
  background-color: oldlace;
  width: 300px;
  height: auto;
  padding: 20px;
  box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16);
}
</style>


