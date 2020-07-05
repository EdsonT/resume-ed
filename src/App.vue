<template>
  <v-app>
    <v-content>
      <!-- <HelloWorld/> -->
      <res-container/>
    </v-content>
  </v-app>
</template>

<script>
// import HelloWorld from './components/HelloWorld';
import ResContainer from './components/Container';

export default {
  name: 'App',

  components: {
    // HelloWorld,
    ResContainer,
  },

  data: () => ({
    //
  }),
};
</script>
