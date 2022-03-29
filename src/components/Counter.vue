<template>
  <h1>{{ customTitle }}</h1>
  <p>This is a counter developed by MateoBetancurB</p>
  <p>{{ counter }}</p>
  <button @click="aumentarSaldo">Aumentar</button>
  <button @click="disminuirSaldo" :desactivar="desactivar">Disminuir</button>
  <button @click="resetearSaldo" :desactivar="desactivar">Resetear</button>
  <h3>{{ notificacion }}</h3>
</template>

<script>
export default {
  props: {
    title: String,
    start: {
      type: Number,
      default: 100,
      validator(value) {
        return value >= 0;
      },
    },
  },
  data() {
    return {
      counter: this.start,
      desactivar: false,
      notificacion: "",
    };
  },
  methods: {
    aumentarSaldo() {
      this.counter = this.counter + 100;
      this.desactivar = false;
      this.notificacion = "";
    },
    disminuirSaldo() {
      if (this.counter === 0) {
        this.desactivar = true;
        this.notificacion = "No puedes restar más";
      } else {
        this.counter = this.counter - 100;
      }
    },
    resetearSaldo() {
      if (this.counter === 0) {
        this.desactivar = true;
        this.notificacion = "El valor ya fue reseteado";
      } else {
        this.counter = this.counter = 0;
        this.notificacion = "Valor reseteado";
      }
    },
  },
  computed: {
    customTitle() {
      return this.title ? this.title : "Counter";
    },
  },
};
</script>

<style>
button {
  border-radius: 15px;
  cursor: pointer;
  margin-left: 10px;
  padding: 10px;
  transition: 0.3;
}
</style>