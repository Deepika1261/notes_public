<template>
  <div class="col-md-6">
    <label>Add your notes here</label>
    <div class="input-group">
        <span class="input-group-text" id="inputGroup-sizing-default">Heading</span>
        <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default" v-model="note_heading">
    </div>
    <div class="input-group">
        <span class="input-group-text">Add Note</span>
        <textarea class="form-control" aria-label="With textarea" v-model="note"></textarea>
    </div>
    <button type="button" v-on:click=addNote()>{{ button_text }}</button>
  </div>
  <hr />
  <div>
    <ul>
    <li class="list-group-item d-flex justify-content-between align-items-start" v-for="note in notes" :key="note.id" v-bind:class="{doneClass : note.id}">
        <div class="ms-2 me-auto">
            <button v-if="!note.edit" type="button" class="btn btn-primary" @click="editNote(note)">Update</button>
            <button v-else type="button" class="btn btn-primary" @click="submitNote(note)">done</button>
            <input v-if="note.edit" v-model="note.note_heading" class="fw-bold">
            <div v-else class="fw-bold">{{note.note_heading}}</div>
            <input v-if="note.edit" v-model="note.note" class="fw-bold">
            <div v-else>{{note.note}}</div>
            <span class="badge bg-primary rounded-pill" @click="deleteNote">X</span>
        </div>
    </li>
    </ul>
  </div>
</template>
<script>
export default{
    data(){
        return{
            button_text:"Add Note",
            note:"",
            note_heading:"",
            id:0,
            notes:[],
            edit:false
        }
    },
    methods:{
        reset(){
            this.note = '',
            this.note_heading = ''
        },
        addNote(){
            let my_note={
                note_heading:this.note_heading,
                note:this.note,
                id: this.id + 1,
                edit:false
            }
            this.notes.push(my_note)
            console.log(this.$refs.name)
            console.log(my_note);
            this.reset()
        },
        deleteNote(the_note){
            const idx = this.notes.indexOf(the_note)
            this.notes.splice(idx,1)
        },
        editNote: function(the_note){
            the_note.edit=true;
          },
        submitNote(the_note){
            console.log(the_note)
            the_note.edit=false
        }
    }

}
</script>