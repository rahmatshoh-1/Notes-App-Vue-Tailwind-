<template>
  <div class="my-5 notes">
    <div class="note" v-for="note in notes" :key="note.id">
      <div class="note_header">
        <p>{{ note.title }}</p>
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
      required:true
    },
  },
};
</script>
<style scoped>
.notes{
    display: flex;
    align-items: center;
    justify-content: space-between;
    flex-wrap: wrap;
    padding: 40px 0;
}
.note{
    width: 48%;
    padding: 18px 20px;
    margin-bottom: 20px;
    background-color: #fff;
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