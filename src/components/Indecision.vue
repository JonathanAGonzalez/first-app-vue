<template>
  <h1>Preguntale a la machine pa</h1>
  <img v-if="image" v-bind:src="image" alt="bg" />
  <div class="bg-dark"></div>

  <div class="indecision-container">
    <input
      v-model="question"
      type="text"
      placeholder="Hazme una pregunta"
      v-on:change="onCaptureValue"
      maxlength="100"
      minlength="5"
    />
    <p>Recuerda terminar con un signo de interrogación</p>
    <div v-if="isValidQuestion">
      <h2>{{ question }}</h2>
      <h1>{{ answer }}</h1>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Indecision',
  data() {
    return {
      question: '',
      image: null,
      answer: '',
      isValidQuestion: false,
    };
  },
  watch: {
    question: function (newQuestion) {
      this.isValidQuestion = false;
      if (!newQuestion.includes('?')) return;
      this.getAnswer();
    },
  },
  methods: {
    onCaptureValue: function (e) {
      this.question = e.target.value;
    },
    async getAnswer() {
      try {
        this.answer = 'Pensando...';
        const { answer, image } = await fetch('https://yesno.wtf/api').then(
          (res) => res.json()
        );
        this.answer = answer === 'yes' ? '!Si' : '!No';
        this.image = image;
        this.isValidQuestion = true;
      } catch (error) {
        console.log(error);
      }
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

.indecision-container {
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
  margin-top: 0px;
}

h1,
h2 {
  color: white;
}

h2 {
  margin-top: 150px;
}
</style>
