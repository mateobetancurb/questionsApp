<template>
  <img v-if="img" :src="img" alt="background image" />
  <div class="bg-dark"></div>
  <div class="questions-container">
    <input v-model="question" type="text" placeholder="Hazme una pregunta" />
    <p>Recuerda terminar con un signo de interrogación (?)</p>
    <div>
      <h1>{{ question }}</h1>
      <h2>Tu respuesta es: {{ answer }}</h2>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      question: null,
      answer: null,
      img: null,
    };
  },
  methods: {
    async getAnswer() {
      this.answer = "Pensando...";
      const { answer, image } = await fetch("https://yesno.wtf/api").then((r) =>
        r.json()
      );
      this.answer = answer;
      this.img = image;
    },
  },
  watch: {
    question(value, oldValue) {
      if (!value.includes("?")) return;
      //Realizar petición http
      this.getAnswer();
    },
  },
};
</script>

<style scoped>
img,
.bg-dark {
  height: 100vh;
  left: 0px;
  max-height: 100%;
  max-width: 100%;
  position: fixed;
  top: 0px;
  width: 100vw;
}

.bg-dark {
  background-color: rgba(0, 0, 0, 0.4);
}

.questions-container {
  position: relative;
  z-index: 99;
}

input {
  width: 250px;
  padding: 10px 15px;
  border-radius: 5px;
  border: none;
}
input:focus {
  outline: none;
}

p {
  color: white;
  font-size: 20px;
  margin-top: 20px;
}

h1,
h2 {
  color: white;
}

h1 {
  margin-top: 100px;
}
</style>