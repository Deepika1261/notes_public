<template>
  <div class="note-nm">
    <div class="note-nm-header">
      <span class="note-nm-close" @click="deleteNote">
        X
      </span>
    </div>
    <div class="note-nm-title" contenteditable="" @blur="titleChanged">
      {{note.title}}
    </div>
    <div class="note-nm-body" contenteditable="" @blur="bodyChanged">
      {{note.body}}
    </div>
  </div>
</template>
<script>

export default({
  name:"MyNote",
    props: {
      note: {
        type: Object,
        required: true
      }
    },
  methods: {
      titleChanged($event) {
        console.log($event.target.innerHtml)
      },
      bodyChanged() {
      },
      deleteNote() {
        this.$emit('deleteNote', this.note);
      } 
    }
});
</script>


<style lang="scss" scoped>
  .note-nm {
    background-color: #f0c806;
    border-radius: 8px;
    width: 280px;
    margin: 0 10px 20px;
    box-shadow: 1px 3px 5px rgba(0, 0, 0, 0.2);
    transition: all 0.5s;
    cursor: pointer;
    font-family: 'Caveat', cursive;
    .note-nm-header {
      padding: 10px 16px 0;
      .note-nm-close {
        display: inline-block;
        width: 24px;
        height: 24px;
        border-radius: 50%;
        line-height: 24px;
        text-align: center;
        transition: all 0.3s;
        &:hover {
          background-color: rgba(0, 0, 0, 0.2);
        }
        &:focus {
          box-shadow: inset 2px 3px 0px rgba(0, 0, 0, 0.8);
        }
      }
      .tc-note-close {
        float: right;
      }
    }
    .note-nm-title,
    .note-nm-body {
      outline: 0;
    }
    .note-nm-title {
      font-size: 24px;
      padding: 10px 16px;
      font-weight: bold;
    }
    .note-nm-body {
      font-size: 20px;
      padding: 10px 16px 16px;
    }
    &:hover {
      box-shadow: 2px 4px 10px rgba(0, 0, 0, 0.3);
    }
  }
</style>