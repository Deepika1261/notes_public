<template>
  <div class="note-wrapper" style="background-image: '.\assets\Capturevs.PNG';">
    <add-new-button @addNote="addNote"/>
    <div class="tc-notes">
      <note v-for="(note, index) in notes" :note="note" :key="index"
            @deleteNote="deleteNote"
            @updateNote="updateNote"/>    
    </div>
  </div>
</template>
<script>
import Note from './Note.vue'
import AddNewButton from './AddNewButton.vue'

export default({
  name:"MyNotes",
  components:{Note,AddNewButton},
  data(){
    return{
      notes:[{
        title:"hello title1",
        body:"hello body1"
      }
      ]
    }
  },
  methods:{
    deleteNote(note) {
          this.notes.splice(this.notes.indexOf(note), 1);
      },
    addNote(){
      this.notes.unshift({title:"",body:""});
    },
    updateNote(note){
      this.note=note
      console.log(this.note)
  }
  },
})
</script>

<style lang="scss">
  .note-wrapper {
    padding-top: 30px;
    .tc-notes {
      display: flex;
      justify-content: center;
      flex-wrap: wrap;
      margin: 0 auto;
    }
  }
</style>