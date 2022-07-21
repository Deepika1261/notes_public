<template>
<v-container class="my-5">
  <v-card flat v-for="note in notes" :key="note.id">
    <v-layout row wrap :class="`pa-2 note ${notes.is_favourite}`">
      <v-flex xs12 md6>
        <div class="caption grey--text text-darken-3">{{note.note_heading}}</div>
        <div>{{ note.note }}</div>
      </v-flex>
      <v-flex xs6 sm4 md2>
        <div class="caption grey--text">Edit</div>
        <v-btn class="ma-2" outlined large fab color="indigo">
            <v-icon>mdi-pencil</v-icon>
        </v-btn>
      </v-flex>
      <v-flex xs6 sm4 md2>
        <div class="caption grey--text">Delete</div>
        <v-btn class="mx-2" fab dark small color="primary">
            <v-icon dark >X</v-icon>
        </v-btn>
      </v-flex>
    </v-layout>
    <v-divider></v-divider>
  </v-card>
</v-container>
</template>
<script>
export default {
  name: "ViewNote",
  data() {
    return {
      notes: [
        { id: 1, is_favourite:false, note_heading: 'Book Writing', note: 'Lorem ipsum dolor sit amet consectetur adipisicinjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjjg elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
        { id: 2, is_favourite:true, note_heading: 'Special holidays', note: 'North East Asia, Goa, Paris, Turkey'},
        { id: 3, is_favourite:false, note_heading: 'Food rich in vitamin D', note: 'Eggs, Fish, Spinach, Beetroot dried nuts'},
        { id: 4, is_favourite:true, note_heading: 'Hockey match', note: 'Lorem ipsum dolor sit amet consectetur adipisicing elit. Sunt consequuntur eos eligendi illum minima adipisci deleniti, dicta mollitia enim explicabo fugiat quidem ducimus praesentium voluptates porro molestias non sequi animi!'},
      ]
    }
  }
}
</script>

<style>
.project.complete{
  border-left: 4px solid #3CD1C2;
}
.project.ongoing{
  border-left: 4px solid orange
}
.project.overdue{
  border-left: 4px solid tomato;
}
</style>