<template>
  <div class="note-add">
    <label>Add your notes here</label>
    <div class="input-group mb-3">
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
    <ul style="margin-top: 1.5rem;">
    <li class="list-group-item d-flex justify-content-between align-items-start" v-for="note in notes" :key="note.id" v-bind:class="{doneClass : note.id}">
        <div class="ms-2 me-auto">
        <div class="fw-bold">{{note.note_heading}}</div>
        {{note.note}}
        </div>
        <span class="badge bg-primary rounded-pill" @click="deleteNote">X</span>
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
            notes:[]
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
                id: this.id + 1
            }
            this.notes.push(my_note)
            console.log(my_note);
            this.reset()
        },
        deleteNote(the_note){
            const idx = this.notes.indexOf(the_note)
            this.notes.splice(idx,1)
        }
    }

}
</script>