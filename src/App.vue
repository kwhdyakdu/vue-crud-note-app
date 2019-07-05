<template>
    <div id="app">
        <div style="color: blue;">
            <h1>grokonez</h1>
            <h3>Note App</h3>
        </div>
        <div class="row">
            <div class="col-sm-6">
                <NotesList 
                  @app-addNote="addNote"
                  @app-changeNote="changeNote"
                  :notes="notes"
                  :activeNote="index" />
            </div>
            <div class="col-sm-6">
                <Note
                  @app-removeNote="removeNote"
                  :note="notes[index]" />
            </div>
        </div>
    </div>
</template>

<script>
import NotesList from "./components/NotesList.vue";
import Note from "./components/Note.vue";

export default {
  name: "app",
  components: {
    NotesList,
    Note
  },
  data: () => ({
    notes: [],
    index: 0
  }),
  methods: {
    addNote() {
      this.notes.push({
        title: "",
        content: ""
      });
      this.index = this.notes.length - 1;
    },
    changeNote(index) {
      this.index = index;
    },
    removeNote() {
      this.notes.splice(this.index, 1);
      this.index = this.index === 0 ? 0 : this.index - 1;
    }
  }
};
</script>

<style>
#app {
  text-align: center;
  max-width: 700px;
}
</style>