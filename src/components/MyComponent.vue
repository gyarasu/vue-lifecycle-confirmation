<template>
  <div>
    {{ message }}
  </div>
</template>

<script>
export default {
  props: {
    param: {
      type: Number,
      required: true,
    },
  },
  data() {
    return {
      message: '',
    };
  },
  beforeCreate() {
    console.log('[beforeCreate]');
  },
  created() {
    console.log('[created]');
  },
  beforeMount() {
    console.log('[beforeMount]');
  },
  mounted() {
    console.log('[mounted]');
    if (this.param === 1) {
      this.message = 'Hello';
    } else {
      this.message = 'こんにちは';
    }
  },
  beforeUpdate() {
    console.log('[beforeUpdate]');
  },
  updated() {
    console.log('[updated]');
  },
  beforeDestroy() {
    console.log('[beforeDestroy]');
  },
  destroyed() {
    console.log('[destroyed]');
  }
}
</script>