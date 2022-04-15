<template>
  <div id="app">
    <div class="container mx-auto">
      <!-- Message Empty -->
      <Message v-if="message" :message="message" />
      <!-- New Note -->
      <NewNote :new_note="new_note" @addNote="addNote" />
      <div class="note_header">
        <h1 class="my-5 text-3xl font-bold text-white">{{ title }}</h1>
          <!-- Search -->
      <Search
        :value="search"
        placeholder="Find your note"
        @search="search = $event"
      />
        <div class="flex justify-between text-center icons">
          <svg
            :class="{ active: grid }"
            @click="grid = true"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <rect x="3" y="3" width="7" height="7"></rect>
            <rect x="14" y="3" width="7" height="7"></rect>
            <rect x="14" y="14" width="7" height="7"></rect>
            <rect x="3" y="14" width="7" height="7"></rect>
          </svg>
          <svg
            :class="{ active: !grid }"
            @click="grid = false"
            xmlns="http://www.w3.org/2000/svg"
            width="24"
            height="24"
            viewBox="0 0 24 24"
            fill="none"
            stroke="currentColor"
            stroke-width="2"
            stroke-linecap="round"
            stroke-linejoin="round"
          >
            <line x1="8" y1="6" x2="21" y2="6"></line>
            <line x1="8" y1="12" x2="21" y2="12"></line>
            <line x1="8" y1="18" x2="21" y2="18"></line>
            <line x1="3" y1="6" x2="3" y2="6"></line>
            <line x1="3" y1="12" x2="3" y2="12"></line>
            <line x1="3" y1="18" x2="3" y2="18"></line>
          </svg>
        </div>
      </div>
    
      <Notes :notes="notesFilter" :grid="grid" @remove="removeNote" />
    </div>
  </div>
</template>

<script>
import Message from "@/components/Message.vue";
import NewNote from "@/components/NewNote.vue";
import Notes from "@/components/Notes.vue";
import Search from "@/components/Search.vue";

export default {
  components: {
    Message,
    NewNote,
    Notes,
    Search,
  },
  data() {
    return {
      title: "Notes App",
      message: null,
      grid: true,
      search: "",
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
    computed:{
    notesFilter () {
      let array = this.notes,
          search = this.search
       if (!search) return array
      //  small
      search = search.trim().toLowerCase()
      // filter
      array = array.filter(function(item){
        if(item.title.toLowerCase().indexOf(search) !== -1){
          return item
        }
      })
      // error
      return array
    }
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
    removeNote(index) {
      this.notes.splice(index, 1);
    },
  },
};
</script>

<style>
body {
  background-color: #25304a;
}
#app {
  font-family: "Montserrat", sans-serif;
}
</style>
