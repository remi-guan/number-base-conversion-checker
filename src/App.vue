<template>
  <v-app>
    <v-main>
      <ConversionChecker/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import Vue from 'vue';
import ConversionChecker from './components/Checker.vue';

export default Vue.extend({
  name: 'App',

  components: {
    ConversionChecker,
  },

  data: () => ({
    //
  }),
});
</script>
