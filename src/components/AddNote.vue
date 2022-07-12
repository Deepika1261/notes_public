<template>
  <div class="col-md-6">
    <label>Add your notes here</label>
    <div class="input-group">
        <span class="input-group-text" id="inputGroup-sizing-default">Heading</span>
        <input type="text" class="form-control" aria-label="Sizing example input" aria-describedby="inputGroup-sizing-default" v-model="note_heading">
    </div>
    <div class="input-group">
        <span class="input-group-text">Note body</span>
        <textarea class="form-control" aria-label="With textarea" v-model="note"></textarea>
    </div>
    <button type="button" v-on:click=addNote()>{{ button_text }}</button>
  </div>
  <hr />
  <div class="col-md-6">
    <ul>
    <li class="list-group-item" v-for="note in notes" :key="note.id" v-bind:class="{doneClass : note.id}">
        <div class="grid-container">
          <div class="item1">
            <button v-if="selected_id!=note.id && selected_note" type="button" class="btn btn-primary" @click="editNote(note)">Update</button>
            <button v-if="selected_id==note.id" type="button" class="btn btn-primary" @click="submitNote(note)">done</button>
          </div>
          <div class="item2">
            <input v-if="selected_id==note.id" v-model="update_heading" class="title-bold">
            <div v-else class="fw-bold"><b>{{note.note_heading}}</b></div>
          </div>
          <div class="item3">
            <input v-if="selected_id==note.id" v-model="update_note" class="body-plain">
            <div v-else>{{note.note}}</div>
          </div>  
          <div class="item4">
            <span class="badge bg-primary rounded-pill" @click="deleteNote(note)">X</span>
          </div>
          <div class="item5">
            <button v-if="selected_id==note.id" type="button" class="btn btn-danger" @click="discardNote(note)">Discard</button>
            <div v-else></div>
          </div>
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
            selected_id:null,
            update_heading:"",
            update_note:"",
            selected_note:true
        }
    },
    methods:{
        reset(){
            this.note = '',
            this.note_heading = ''
            this.id=this.id+1
        },
        addNote(){
            let my_note={
                note_heading:this.note_heading,
                note:this.note,
                id: this.id,
                edit:false
            }
            this.notes.push(my_note)
            this.reset()
        },
        deleteNote(the_note){
            const idx = this.notes.indexOf(the_note)
            console.log(idx)
            this.notes.splice(idx,1)
        },
        editNote: function(the_note){
            this.selected_id=the_note.id;
            this.update_heading=the_note.note_heading;
            this.selected_note=false;
            this.update_note=the_note.note;
            console.log(this.selected_note)
          },
        submitNote(note){
            note.note_heading=this.update_heading
            note.note=this.update_note
            this.selected_note=true;
            this.selected_id=null
            console.log(this.selected_note)
        },
        discardNote(note){
            this.selected_id=null
            this.selected_note=true;
            console.log(note)
            console.log(this.selected_note)
        }
    }

}
</script>
<style scoped>
        .item1 { grid-area: update; }
        .item2 { grid-area: title; }
        .item3 { grid-area: body; }
        .item4 { grid-area: delete; }
        .item5 { grid-area: discard; }
        .grid-container {
          display: grid;
          grid-template-areas:
            'update title title title delete '
            'discard body body body delete';
          grid-template-columns: 20% 57% 20%;
          gap: 3px;
          padding: 5px;
        }
    
        .item{
            margin: 0%;
            padding:0%;
        }
        .title-bold .body-plain{
            align-self: flex-start;
        }
</style>