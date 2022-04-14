<template>
  <!-- add New note -->
  <div class="new_note">
      <label>Tittle</label>
    <input
      type="text"
      v-model="new_note.title"
      class="w-full px-4 py-2 leading-tight text-gray-700 bg-gray-100 border-2 border-gray-200 rounded appearance-none focus:outline-none focus:bg-green-100 focus:border-green-200"
    />
      <label>Description</label>
    <textarea
      v-model="new_note.desc"
      class="w-full px-4 py-2 my-5 leading-tight text-gray-700 bg-gray-100 border-2 border-gray-200 rounded appearance-none focus:outline-none focus:bg-green-100 focus:border-green-200"
    >
    </textarea>
    <button
      @click="addNote"
      class="p-3 text-green-500 transition duration-500 bg-green-100 rounded hover:bg-green-300 hover:text-green-700"
    >
      Add new Note
    </button>
  </div>
  <!-- new note End -->
</template>
<script>
export default {
    props:{
        new_note:{
            type:Object,
            required:true
        }
    },
    methods:{
        addNote(){
            this.$emit('addNote', this.new_note)
        }
    }
}
</script>