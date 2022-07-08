<template>
<h1>{{heading}}</h1>
  <AddNote />
</template>

<script>
import AddNote from './components/AddNote.vue'

export default {
  name: 'App',
  components: {
    AddNote
  },
  data(){
    return {
      heading: "TAKE NOTES"
      }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
