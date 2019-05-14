<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <my-component :param=1 v-if="comp1"></my-component>
    <my-component :param=2 v-if="comp2"></my-component>
    <button v-on:click="switch1">normal</button>
    <button v-on:click="switch2">new thread</button>
    <button v-on:click="reset">reset</button>
  </div>
</template>

<script>
import MyComponent from './components/MyComponent.vue'

export default {
  name: 'app',
  components: {
    'my-component': MyComponent,
  },
  data() {
    return {
      comp1: true,
      comp2: false,
    };
  },
  methods: {
    switch1() {
      // my-component for 'param=2' won't be mounted
      this.comp1 = false;
      this.comp2 = true;
    },
    switch2() {
      this.comp1 = false;

      // my-component for 'param=2' will be mounted
      setTimeout(() => {
        this.comp2 = true;
      }, 1);
    },
    reset() {
      location.reload();
    },
  }
};
</script>

<style>
</style>
