<template>
  <div class="my-5 notes">
    <div class="note" v-for="(note, index) in notes" :key="index">
      <div class="note_header">
        <p>{{ note.title }}</p>
        <p class="cursor-pointer" @click="removeNote(index)">x</p>
      </div>
      <div class="note_body">
        <p>{{ note.desc }}</p>
        <span>{{ note.date }}</span>
      </div>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    notes: {
      type: Array,
      required: true,
    },
  },
  methods: {
    removeNote(index) {
      console.log(`Note id -${index} removed`);
      this.$emit("remove", index);
    },
  },
};
</script>
<style scoped>
.notes {
  display: flex;
  align-items: center;
  justify-content: space-between;
  flex-wrap: wrap;
  padding: 40px 0;
}
.note {
  width: 48%;
  padding: 18px 20px;
  margin-bottom: 20px;
  background-color: #fff;
}
.note_header {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.note_header p {
  font-size: 22px;
  color: #54eb9c;
}
.note_body p {
  margin: 20px 0;
}
.note_body span {
  font-size: 14px;
  color: #999;
}
</style>
