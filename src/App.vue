<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <my-component :param=1 v-if="comp1"></my-component>
    <my-component :param=2 v-if="comp2"></my-component>
    <button v-on:click="switch1">normal</button>
    <button v-on:click="switch2">new thread</button>
    <button v-on:click="switch3">next tick</button>
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
      // my-component for 'param=1' won't be destroyed
      // my-component for 'param=2' won't be mounted
      this.comp1 = false;
      this.comp2 = true;
    },
    switch2() {
      // my-component for 'param=1' will be destroyed
      this.comp1 = false;

      // my-component for 'param=2' will be mounted
      setTimeout(() => {
        this.comp2 = true;
      }, 1);
    },
    switch3() {
      // my-component for 'param=1' will be destroyed
      this.comp1 = false;

      // my-component for 'param=2' will be mounted
      this.$nextTick(() => {
        this.comp2 = true;
      });
    },
    reset() {
      location.reload();
    },
  }
};
</script>

<style>
</style>
