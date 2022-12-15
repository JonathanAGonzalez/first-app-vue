<template>
  <h2>{{ customTitle }}</h2>
  <p>{{ count }} <sup>2</sup> = {{ totalSquare }}</p>
  <div class="wrapper__container">
    <button v-on:click="increase">Suma</button>
    <button v-on:click="decrease">Resta</button>
  </div>
</template>

<script>
export default {
  name: 'Counter',
  props: {
    title: String,
    start: {
      type: Number,
      required: true,
      default: 1,
      validator(value) {
        return value >= 10;
      },
    },
  },
  data() {
    return {
      count: this.start,
    };
  },

  methods: {
    increase() {
      this.count++;
    },
    decrease() {
      if (this.count > 0) {
        this.count--;
      }
    },
  },
  computed: {
    totalSquare() {
      return this.count * this.count;
    },
    customTitle() {
      return this.title || 'Counter';
    },
  },
};
</script>

<style>
.wrapper__container {
  align-items: center;
  display: flex;
  gap: 30px;
  justify-content: center;
}
</style>
