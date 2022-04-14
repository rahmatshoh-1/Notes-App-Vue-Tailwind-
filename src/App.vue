<template>
  <div id="app">
    <div class="container mx-auto">
      <h1 class="my-5 text-4xl font-bold">Notes app</h1>
     <!-- Message Empty -->
      <Message v-if="message" :message="message" />
      <!-- New Note -->
      <NewNote :new_note="new_note" @addNote="addNote" />
      
      <Notes :notes="notes" @remove="removeNote"/>
    </div>
  </div>
</template>

<script>
import Message from "@/components/Message.vue";
import NewNote from "@/components/NewNote.vue";
import Notes from "@/components/Notes.vue";
export default {
  components: {
    Message,
    NewNote,
    Notes,
  },
  data() {
    return {
      title: "Notes App",
      message: null,
      new_note: {
        title: "",
        desc: "",
      },
      notes: [
        {
          id: 1,
          title: "First note",
          desc: "Description for first note",
          date: new Date(Date.now()).toLocaleString("en-GB"),
        },
        {
          id: 2,
          title: "Second note",
          desc: "Description for second note",
          date: new Date(Date.now()).toLocaleString("en-GB"),
        },
        {
          id: 3,
          title: "Third note",
          desc: "Description for third note",
          date: new Date(Date.now()).toLocaleString("en-GB"),
        },
      ],
    };
  },

  methods: {
    addNote() {
      // console.log(this.new_note);
      let { title, desc } = this.new_note;

      if (title === "") {
        this.message = "title can't be blank !";
        return false;
      }

      this.notes.push({
        title,
        desc,
        date: new Date(Date.now()).toLocaleString("en-GB"),
      });

      this.message = null;
      this.new_note.title = "";
      this.new_note.desc = "";
    },
    removeNote(index){
      this.notes.splice(index,1)
    }
  },
};
</script>

<style>
body {
  background-color: #f2f2f2;
}
#app {
  font-family: "Montserrat", sans-serif;
}
</style>
