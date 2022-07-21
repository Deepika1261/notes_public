<template>
  <v-app class="yellow">
      <HelloWorld/>
      <ViewNote/>
  </v-app>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import ViewNote from './components/ViewNotes.vue'

export default {
  name: 'App',

  components: {
    HelloWorld,
    ViewNote,
},

  data: () => ({
    //
  }),
};
</script>
