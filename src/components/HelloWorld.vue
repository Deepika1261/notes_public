<template>
<nav>
  <v-toolbar flat app>
    <v-app-bar-nav-icon @click="drawer = !drawer" class="grey--text"></v-app-bar-nav-icon>
    <v-toolbar-title class="display-2 grey--text">
      <span class="font-weight-light">Add</span>
      <span>Notes</span>
    </v-toolbar-title>
  </v-toolbar>
  <v-navigation-drawer width="500" app v-model="drawer" class="indigo lighten-4">
  <div></div>
  <div></div>
  <hr />
  <form>
    <v-text-field v-model="note_heading" label="HEADING" required></v-text-field>
    <v-text-field v-model="note" label="BODY" required></v-text-field>
    <v-btn class="mr-4">submit</v-btn>
    <v-btn >clear</v-btn>
  </form>
  </v-navigation-drawer>
</nav>

</template>

<script>
  export default {
    name: 'HelloWorld',

    data(){
      return{
        note:"",
        note_heading:"",
        drawer:false,
      }
    }
  }
</script>
