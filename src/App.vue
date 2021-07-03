<template>
  <div class="content">
    <Calculator />
  </div>
</template>

<script>
import Calculator from './components/Calculator.vue';

export default {
  name: 'App',
  components: {
    Calculator,
  },
};
</script>

<style lang="scss">

@import url('https://fonts.googleapis.com/css2?family=Inter&display=swap');

html,
body {
  margin: 0;
  padding: 0;
  font-family: 'Inter', sans-serif;
}
.content{
  height: 100vh;
  width: 100vw;
  position: relative;
}
</style>
