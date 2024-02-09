<template>
  <the-header title="Remember Me"></the-header>

  <the-resources></the-resources>
</template>

<script>
import TheHeader from './components/layout/TheHeader.vue';
import TheResources from './components/Learning-Resources/TheResources.vue';

export default {
  components: {
    TheHeader,
    TheResources,
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Poppins:wght@300&display=swap');

* {
  box-sizing: border-box;
  font-family: Poppins;
}

html {
  font-family: 'Roboto', sans-serif;
}

body {
  margin: 0;
}
</style>
